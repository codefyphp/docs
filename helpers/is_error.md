Description
-----------

Check whether variable is an Error instance.

Usage
-----

    <?php

    use function Qubus\Error\Helpers\is_error;
    
    is_error(mixed $object): bool;

Parameters
----------

**$object** (mixed) The object to check.

Return Value
------------

(bool) True if an Error instance, false otherwise.

Example
-------

    <?php

    use Qubus\Error\Error;
    
    use function Qubus\Error\Helpers\is_error;
    
    function has_permission(string $permission): Error|string
    {
        if ($permission === 'invalid') {
            return new Error('The permission value is invalid');
        }
        
        return $permission;
    }
    
    $permission = has_permission('invalid');
    
    if (is_error($permission)) {
        echo $permission->getMessage();
    }