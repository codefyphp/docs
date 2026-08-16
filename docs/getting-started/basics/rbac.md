---
title: Role-Based Access Control
sidebar_title: RBAC
weight: 14
---

## Installation

```shell
composer require codefyphp/codefy
```

The Role-Based Access Control (RBAC) component provides role-based authorization abstraction for the CodefyPHP Framework.

## Introduction

[Role-Based Access Control](https://en.wikipedia.org/wiki/Role-based_access_control) (RBAC) is based on the idea of roles rather than permissions as you may find in ACL. 
In a web application, users will typically have identities defined by `username`, `email`, `token`, etc.

RBAC System:

* An Identity has one or more roles
* A role requests access to a permission
* A permission is given to a role

Thus RBAC has:

* Many-to-many relationship between identities and roles.
* Many-to-many relationship between roles and permissions.
* Roles can have a parent role.

To get started, there are 2 ways to store role and permission settings: persistently by extending `BaseStorageResource` 
or by runtime using `./config/rbac.php`.

## BaseStorageResource

Here is a sample code of `FileResource` which extends the `BaseStorageResource` abstraction:

```php
<?php

declare(strict_types=1);

namespace Application\Service;

use Codefy\Framework\Auth\Rbac\Resource\BaseStorageResource;

final class FileResource extends BaseStorageResource
{
    /**
     * @var string
     */
    protected string $file;

    /**
     * @param string $file
     */
    public function __construct(string $file)
    {
        $this->file = $file;
    }

    /**
     * @throws SentinelException
     * @throws FilesystemException
     */
    public function load(): void
    {
        $this->clear();

        if (!file_exists($this->file) || (!$data = LocalStorage::disk()->read(json_decode($this->file, true)))) {
            $data = [];
        }

        $this->restorePermissions($data['permissions'] ?? []);
        $this->restoreRoles($data['roles'] ?? []);
    }

    /**
     * @throws FilesystemException
     */
    public function save(): void
    {
        $data = [
            'roles' => [],
            'permissions' => [],
        ];
        foreach ($this->roles as $role) {
            $data['roles'][$role->getName()] = $this->roleToRow($role);
        }
        foreach ($this->permissions as $permission) {
            $data['permissions'][$permission->getName()] = $this->permissionToRow($permission);
        }

        LocalStorage::disk()->write($this->file, json_encode(value: $data, flags: JSON_PRETTY_PRINT));
    }

    protected function roleToRow(Role $role): array
    {
        $result = [];
        $result['name'] = $role->getName();
        $result['description'] = $role->getDescription();
        $childrenNames = [];
        foreach ($role->getChildren() as $child) {
            $childrenNames[] = $child->getName();
        }
        $result['children'] = $childrenNames;
        $permissionNames = [];
        foreach ($role->getPermissions() as $permission) {
            $permissionNames[] = $permission->getName();
        }
        $result['permissions'] = $permissionNames;
        return $result;
    }

    protected function permissionToRow(Permission $permission): array
    {
        $result = [];
        $result['name'] = $permission->getName();
        $result['description'] = $permission->getDescription();
        $childrenNames = [];
        foreach ($permission->getChildren() as $child) {
            $childrenNames[] = $child->getName();
        }
        $result['children'] = $childrenNames;
        $result['ruleClass'] = $permission->getRuleClass();
        return $result;
    }

    /**
     * @throws SentinelException
     */
    protected function restorePermissions(array $permissionsData): void
    {
        /** @var string[][] $permChildrenNames */
        $permChildrenNames = [];

        foreach ($permissionsData as $pData) {
            $permission = $this->addPermission($pData['name'] ?? '', $pData['description'] ?? '');
            $permission->setRuleClass($pData['ruleClass'] ?? '');
            $permChildrenNames[$permission->getName()] = $pData['children'] ?? [];
        }

        foreach ($permChildrenNames as $permissionName => $childrenNames) {
            foreach ($childrenNames as $childName) {
                $permission = $this->getPermission($permissionName);
                $child = $this->getPermission($childName);
                if ($permission && $child) {
                    $permission->addChild($child);
                }
            }
        }
    }

    /**
     * @throws SentinelException
     */
    protected function restoreRoles($rolesData): void
    {
        /** @var string[][] $rolesChildrenNames */
        $rolesChildrenNames = [];

        foreach ($rolesData as $rData) {
            $role = $this->addRole($rData['name'] ?? '', $rData['description'] ?? '');
            $rolesChildrenNames[$role->getName()] = $rData['children'] ?? [];
            $permissionNames = $rData['permissions'] ?? [];
            foreach ($permissionNames as $permissionName) {
                if ($permission = $this->getPermission($permissionName)) {
                    $role->addPermission($permission);
                }
            }
        }

        foreach ($rolesChildrenNames as $roleName => $childrenNames) {
            foreach ($childrenNames as $childName) {
                $role = $this->getRole($roleName);
                $child = $this->getRole($childName);
                if ($role && $child) {
                    $role->addChild($child);
                }
            }
        }
    }
}
```

## Usage
We can now initiate with our FileResource. The resource can be a file, database, cache or runtime. You can extend the 
`BaseStorageResource` or create an implementation of `Codefy\Framework\Auth\Rbac\Resource\StorageResource`.

```php
<?php

use Application\Service\FileResource;
use Codefy\Framework\Auth\Rbac\Rbac;

$resource = new FileResource('rbac.json');
$rbac = new Rbac($resource);
```

### Create Permissions Hierarchy

```php
<?php

$perm1 = $rbac->addPermission('create_post', 'Can create posts');
$perm2 = $rbac->addPermission('moderate_post', 'Can moderate posts');
$perm3 = $rbac->addPermission('update_post', 'Can update posts');
$perm4 = $rbac->addPermission('delete_post', 'Can delete posts');
$perm2->addChild($perm3); // moderator can also update
$perm2->addChild($perm4); // and delete posts
```

### Create Role Hierarchy

```php
<?php

$adminRole = $rbac->addRole('admin');
$moderatorRole = $rbac->addRole('moderator');
$authorRole = $rbac->addRole('author');
$adminRole->addChild($moderatorRole); // admin has all moderator's rights
```

!!! warning "Important!"
    Please note that when defining roles and permissions, permissions should be added and loaded before roles.

### Bind Roles and Permissions

```php
<?php

...
$moderatorRole->addPermission($perm2);
...
```

### Persist State

```php
<?php

$rbac->save();
```

### Checking Access Rights

```php
<?php

if($rbac->getRole($user->role)->checkAccess('moderate_post') {
    ... // User can moderate posts
}
// or add to your user's class something like:
$user->can('moderate_post');
```

## Rules

Sometimes you need to perform an extra check. For example, what if you only want authors to `edit`, `update` or `delete` 
their own content, but not someone else's content? You can do that by setting a rule. You can do so by implementing 
the `AssertionRule` interface with the `execute()` method.

```php title="./src/Domain/Post/Service/AuthorRule.php"
<?php

declare(strict_types=1);

namespace Domain\Post\Service;

use Codefy\Framework\Auth\Rbac\Entity\AssertionRule;

final class AuthorRule implements AssertionRule
{

    /**
     * @param array|null $params
     *
     * @return bool
     */
    public function execute(?array $params = null): bool
    {
        // @var Post $post
        if($post = $params['post'] ?? null) {
            return $post->authorId === ($params['userId'] ?? null);
        }
        return false;
    }
}
```

### Configure RBAC

```php
<?php

use Domain\Post\Service\AuthorRule;

$perm5 = $rbac->addPermission('post:author_update', 'Author can update his posts.');
$perm6 = $rbac->addPermission('post:author_delete', 'Author can delete his posts.');
$perm5->setRuleClass(AuthorRule::class);
$perm6->setRuleClass(AuthorRule::class);
$authorRole->addPermission($perm5);
$authorRole->addPermission($perm6);
```

### Check Rights

```php
<?php

if($rbac->checkAccess('post:author_delete', ['userId' => $userId, 'post' => $post]) {
    ... // The user is author of the post and can delete it
}
```
    
## RBAC Config

The alternative to using a resource is setting up a config to be checked during runtime.

```php title="./config/rbac.php"
<?php

use Domain\Post\Service\AuthorRule;

return [

    'permissions' => [
        'admin' => [
            'description' => 'Super Admin',
            'permissions' => [
                'admin:dashboard' => ['description' => 'Access to the dashboard.'],
                'admin:profile' => ['description' => 'Access to profile edit.'],
                'admin:edit_post' => ['description' => 'Edit posts.', 'ruleClass' => AuthorRule::class],
            ],
        ],
    ],

    'roles' => [
        'user' => [
            'description' => 'Regular user',
            'permissions' => [],
        ],
        'manager' => [
            'description' => 'Editor',
            'permissions' => ['admin:dashboard'],
        ],
        'admin' => [
            'description' => 'Administrator',
            'permissions' => ['admin'],
        ],
    ],
];
```

If you use the config option, you will need to figure out a way to load them during runtime so that it can be checked 
against the user. The skeleton app conveniently includes a [loader](https://github.com/codefyphp/codefy/blob/3.0.x/src/Auth/Rbac/RbacLoader.php) as well as a 
[service provider](https://github.com/codefyphp/skeleton/blob/2.x/App/Infrastructure/Providers/RbacServiceProvider.php) 
to load `roles` and `permissions` during runtime. If you want to change, edit, or add permissions and roles, check out 
`File: ./config/rbac.php`.

!!! warning "Important:" 
    As mentioned previously, permissions need to be defined first, and only once. Permissions from any defined group can 
    be used when you define your roles. To use all the permissions from a group, add the key(s) `['admin']` to your array. 
    If you are only wanting to use a particular defined permission from a group, use the specific key(s) in your 
    array `['admin:dashboard']`.

## Authorizing Users

Codefy provides several middlewares for checking and validating user roles, permissions, and session handling.

If you need to check whether a user is authorized to view a certain page, you will need to add  
`Codefy\Framework\Http\Middleware\Auth\UserAuthorizationMiddleware` or the [Injector](../dependency-injection.md) alias (`user.authorization`) 
to your route:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return (function(\Qubus\Routing\Psr7Router $router) {
    $router->get('/admin/', 'AdminController@index')->middleware('user.authorization');
});
```

When a user visits the `/admin/dashboard/` route, the middleware will check if the user is logged in. If the user is 
logged in, the user will continue on, otherwise, the user will be redirected to your login route via the 
`redirect_guests_to` setting in `./config/auth.php`.

A different approach would be to check permissions via the controller. You can use the `Codefy\Framework\Helpers\gate` 
helper or the [Gate Middleware](../../blog/posts/gate-middleware.md):

```php title="./src/Application/Http/Controller/AdminController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Codefy;
use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;

use function Codefy\Framework\Helpers\gate;
use function Codefy\Framework\Helpers\trans;
use function Codefy\Framework\Helpers\view;

final class AdminController extends BaseController
{
    public function index(): ResponseInterface
    {
        if (false === gate(permission: 'admin:dashboard')) {
            Codefy::$PHP->flash->error(
                message: 'You must be logged in to access the admin area.'
            );
            return $this->redirect($this->router->url(name: 'auth.login'));
        }

        return view(
            template: 'framework::backend/index',
            data: ['title' => trans('Dashboard')]
        );
    }
}
```

If you use the gate middleware, then your controller becomes cleaner by adding the gate middleware to your route:

```php title="./routes/web/admin.php"
<?php

declare(strict_types=1);

return (function(\Qubus\Routing\Psr7Router $router) {
    $router->get('/admin/', 'AdminController@index')->middleware(['gate:admin:dashboard,/login/']);
});
```

```php title="./src/Application/Http/Controller/AdminController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;

use function Codefy\Framework\Helpers\trans;
use function Codefy\Framework\Helpers\view;

final class AdminController extends BaseController
{
    public function index(): ResponseInterface
    {
        return view(
            template: 'framework::backend/index',
            data: ['title' => trans('Dashboard')]
        );
    }
}
```

`gate(permission: 'admin:dashboard')` is what's used to check if a logged-in user 
has a certain permission to continue.

Here is a list of other authentication middlewares along with their aliases:

* `Codefy\Framework\Http\Middleware\Auth\ExpireUserSessionMiddleware`
    * __Alias:__ `user.session.expire`
    * __Description:__ This middleware can be used for a logout route to clear the user's session and cookie.
* `Codefy\Framework\Http\Middleware\Auth\AuthenticationMiddleware`
    * __Alias:__ `user.authenticate`
    * __Description:__ This middleware can be used for a login route which checks the submitted login credentials against the database.
* `Codefy\Framework\Http\Middleware\Auth\UserSessionMiddleware`
    * __Alias:__ `user.session`
    * __Description:__ This middleware should be used with the previous middleware. If authentication is successful, the user session and cookie will be created.