***

# InjectorException





* Full name: `\Qubus\Injector\InjectorException`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`E_NON_EMPTY_STRING_ALIAS`|public| |1|
|`M_NON_EMPTY_STRING_ALIAS`|public| |&#039;Invalid alias: non-empty string required at arguments 1 and 2&#039;|
|`E_SHARED_CANNOT_ALIAS`|public| |2|
|`M_SHARED_CANNOT_ALIAS`|public| |&#039;Cannot alias class %s to %s because it is currently shared&#039;|
|`E_SHARE_ARGUMENT`|public| |3|
|`M_SHARE_ARGUMENT`|public| |&#039;%s::share() requires a string class name or 
                                            object instance at Argument 1; %s specified&#039;|
|`E_ALIASED_CANNOT_SHARE`|public| |4|
|`M_ALIASED_CANNOT_SHARE`|public| |&#039;Cannot share class %s because it is currently aliased to %s&#039;|
|`E_INVOKABLE`|public| |5|
|`M_INVOKABLE`|public| |&#039;Invalid invokable: callable or provisional string required&#039;|
|`E_NON_PUBLIC_CONSTRUCTOR`|public| |6|
|`M_NON_PUBLIC_CONSTRUCTOR`|public| |&#039;Cannot instantiate public/public constructor in class %s&#039;|
|`E_NEEDS_DEFINITION`|public| |7|
|`M_NEEDS_DEFINITION`|public| |&#039;Injection definition required for %s %s&#039;|
|`E_MAKE_FAILURE`|public| |8|
|`M_MAKE_FAILURE`|public| |&#039;Could not make %s: %s&#039;|
|`E_UNDEFINED_PARAM`|public| |9|
|`M_UNDEFINED_PARAM`|public| |&#039;No definition available to provision typeless parameter $%s 
                                            at position %d in %s(). Injection Chain: %s&#039;|
|`E_DELEGATE_ARGUMENT`|public| |10|
|`M_DELEGATE_ARGUMENT`|public| |&#039;%s::delegate expects a valid callable or executable class::method 
                                            string at Argument 2%s&#039;|
|`E_CYCLIC_DEPENDENCY`|public| |11|
|`M_CYCLIC_DEPENDENCY`|public| |&#039;Detected a cyclic dependency while provisioning %s&#039;|
|`E_MAKING_FAILED`|public| |12|
|`M_MAKING_FAILED`|public| |&#039;Making %s did not result in an object, instead result is of type \&#039;%s\&#039;&#039;|



***
> Automatically generated on 2025-10-13
