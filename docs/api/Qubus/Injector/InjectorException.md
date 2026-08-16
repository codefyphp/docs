# InjectorException

***

* Full name: `\Qubus\Injector\InjectorException`

## Constants


| Constant                   | Visibility | Type | Value                                                                                                                                                  |
|----------------------------|------------|------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `E_NON_EMPTY_STRING_ALIAS` | public     |      | 1                                                                                                                                                      |
| `M_NON_EMPTY_STRING_ALIAS` | public     |      | 'Invalid alias: non-empty string required at arguments 1 and 2'                                                                                        |
| `E_SHARED_CANNOT_ALIAS`    | public     |      | 2                                                                                                                                                      |
| `M_SHARED_CANNOT_ALIAS`    | public     |      | 'Cannot alias class %s to %s because it is currently shared'                                                                                           |
| `E_SHARE_ARGUMENT`         | public     |      | 3                                                                                                                                                      |
| `M_SHARE_ARGUMENT`         | public     |      | '%s::share() requires a string class name or 
                                            object instance at Argument 1; %s specified'                 |
| `E_ALIASED_CANNOT_SHARE`   | public     |      | 4                                                                                                                                                      |
| `M_ALIASED_CANNOT_SHARE`   | public     |      | 'Cannot share class %s because it is currently aliased to %s'                                                                                          |
| `E_INVOKABLE`              | public     |      | 5                                                                                                                                                      |
| `M_INVOKABLE`              | public     |      | 'Invalid invokable: callable or provisional string required'                                                                                           |
| `E_NON_PUBLIC_CONSTRUCTOR` | public     |      | 6                                                                                                                                                      |
| `M_NON_PUBLIC_CONSTRUCTOR` | public     |      | 'Cannot instantiate public/public constructor in class %s'                                                                                             |
| `E_NEEDS_DEFINITION`       | public     |      | 7                                                                                                                                                      |
| `M_NEEDS_DEFINITION`       | public     |      | 'Injection definition required for %s %s'                                                                                                              |
| `E_MAKE_FAILURE`           | public     |      | 8                                                                                                                                                      |
| `M_MAKE_FAILURE`           | public     |      | 'Could not make %s: %s'                                                                                                                                |
| `E_UNDEFINED_PARAM`        | public     |      | 9                                                                                                                                                      |
| `M_UNDEFINED_PARAM`        | public     |      | 'No definition available to provision typeless parameter $%s 
                                            at position %d in %s(). Injection Chain: %s' |
| `E_DELEGATE_ARGUMENT`      | public     |      | 10                                                                                                                                                     |
| `M_DELEGATE_ARGUMENT`      | public     |      | '%s::delegate expects a valid callable or executable class::method 
                                            string at Argument 2%s'                |
| `E_CYCLIC_DEPENDENCY`      | public     |      | 11                                                                                                                                                     |
| `M_CYCLIC_DEPENDENCY`      | public     |      | 'Detected a cyclic dependency while provisioning %s'                                                                                                   |
| `E_MAKING_FAILED`          | public     |      | 12                                                                                                                                                     |
| `M_MAKING_FAILED`          | public     |      | 'Making %s did not result in an object, instead result is of type \'%s\''                                                                              |
