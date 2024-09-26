The Role-Based Access Control (RBAC) component provides role-based authorization abstraction for the CodefyPHP Framework.

## Introduction
[Role-Based Access Control](https://en.wikipedia.org/wiki/Role-based_access_control) (RBAC) is based on the idea of roles rather than permissions as you may find in ACL. In a web application, users will typically have identities defined by `username`, `email`, `token`, etc.

RBAC System:

- An Identity has one or more roles
- A role requests access to a permission
- A permission is given to a role

Thus RBAC has:

- Many-to-many relationshiop between identities and roles.
- Many-to-many relationship between roles and permissions.
- Roles can have a parent role.

To get started, there are 2 ways to store role and permission settings: persistently by extending `BaseStorageResource` or by runtime using `config/rbac.php`.

## BaseStorageResource

Here is a sample of code of FileResource which extends the `BaseStorageResource` abstraction:

    <?php

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

## Usage
We can now initiate with our FileResource. The resource can be a file, database, cache or runtime. You can extend the BaseStorageResource or create it by implementing `Codefy\Framework\Auth\Rbac\Resource\BaseStorageResource`.

    <?php

    use Codefy\Framework\Auth\Rbac\Rbac;

    $resource = new FileResource('rbac.json');
    $rbac = new Rbac($resource);

### Create Permissions Hierarchy

__Please note that permissions should be added and loaded before roles.__

    <?php

    $perm1 = $rbac->addPermission('create_post', 'Can create posts');
    $perm2 = $rbac->addPermission('moderate_post', 'Can moderate posts');
    $perm3 = $rbac->addPermission('update_post', 'Can update posts');
    $perm4 = $rbac->addPermission('delete_post', 'Can delete posts');
    $perm2->addChild($p3); // moderator can also update
    $perm2->addChild($p4); // and delete posts

### Create Role Hierarchy

    <?php

    $adminRole = $rbac->addRole('admin');
    $moderatorRole = $rbac->addRole('moderator');
    $authorRole = $rbac->addRole('author');
    $adminRole->addChild($moderatorRole); // admin has all moderator's rights

### Bind Roles and Permissions

    <?php

    ...
    $moderatorRole->addPermission($p2);
    ...

### Persist State

    <?php

    $rbac->save();

### Checking Access Rights

    <?php

    if($rbac->getRole($user->role)->checkAccess('moderate_post') {
        ... // User can moderate posts
    }
    // or add to your user's class something like:
    $user->can('moderate_post');

## Rules

Sometimes you need to perform an extra check. For example, what if you only want authors to edit, update or delete posts their own content but not someone elses content? You can do that by setting a rule. You can do so by implementing the `AssertionRule` interface with the `execute` method.

    <?php

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

### Configure RBAC

    <?php

    $perm5 = $rbac->addPermission('post:author_update', 'Author can update his posts.');
    $perm6 = $rbac->addPermission('post:author_delete', 'Author can delete his posts.');
    $perm5->setRuleClass(AuthorRule::class);
    $perm6->setRuleClass(AuthorRule::class);
    $authorRole->addPermission($perm5);
    $authorRole->addPermission($perm6);

### Check Rights

    <?php

    if($rbac->checkAccess('post:author_delete', ['userId' => $userId, 'post' => $post]) {
        ... // The user is author of the post and can delete it
    }
    
## RBAC Config

The alternative to using a resource is setting up a config to be checked during runtime.

    <?php

    return [

        'permissions' => [
            'admin' => [
                'description' => 'Super Admin',
                'permissions' => [
                    'admin:dashboard' => ['description' => 'Access to the dashboard.'],
                    'admin:profile' => ['description' => 'Access to profile edit.'],
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

If you use the config option, you will need to figure out a way to load them during runtime so that it can be checked against the logged in user. You can check out the CodefyPHP skeleton for examples of a [loader](https://github.com/codefyphp/skeleton/blob/2.x/App/Infrastructure/Services/RbacLoader.php) as well as how it is loaded via a [service provider](https://github.com/codefyphp/skeleton/blob/2.x/App/Infrastructure/Providers/RbacServiceProvider.php).