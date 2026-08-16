
***

# Documentation



This is an automatically generated documentation for **Documentation**.

## Namespaces

### \Qubus\Http

#### Classes

| Class                                                                  | Description                                   |
|------------------------------------------------------------------------|-----------------------------------------------|
| [`HttpPublisher`](./HttpPublisher.md)               | StreamPublisher publishes the given response. |
| [`Request`](./Request.md)                           |                                               |
| [`RequestHandler`](./RequestHandler.md)             |                                               |
| [`Response`](./Response.md)                         |                                               |
| [`ServerRequest`](./ServerRequest.md)               |                                               |
| [`ServerRequestFactory`](./ServerRequestFactory.md) |                                               |
| [`Status`](./Status.md)                             |                                               |
| [`Url`](./Url.md)                                   |                                               |

#### Interfaces

| Interface                                        | Description |
|--------------------------------------------------|-------------|
| [`Publisher`](./Publisher.md) |             |

### \Qubus\Http\Cookies

#### Classes

| Class                                                                                | Description |
|--------------------------------------------------------------------------------------|-------------|
| [`CookieCollection`](./Cookies/CookieCollection.md)               |             |
| [`Cookies`](./Cookies/Cookies.md)                                 |             |
| [`CookiesRequest`](./Cookies/CookiesRequest.md)                   |             |
| [`CookiesResponse`](./Cookies/CookiesResponse.md)                 |             |
| [`RequestCookieDecryptor`](./Cookies/RequestCookieDecryptor.md)   |             |
| [`ResponseCookieEncryptor`](./Cookies/ResponseCookieEncryptor.md) |             |
| [`SameSite`](./Cookies/SameSite.md)                               |             |
| [`SetCookieCollection`](./Cookies/SetCookieCollection.md)         |             |
| [`SetCookies`](./Cookies/SetCookies.md)                           |             |
| [`Util`](./Cookies/Util.md)                                       |             |

### \Qubus\Http\Cookies\Factory

#### Classes

| Class                                                                    | Description |
|--------------------------------------------------------------------------|-------------|
| [`CookieFactory`](./Cookies/Factory/CookieFactory.md) |             |

#### Interfaces

| Interface                                                                        | Description |
|----------------------------------------------------------------------------------|-------------|
| [`HttpCookieFactory`](./Cookies/Factory/HttpCookieFactory.md) |             |

### \Qubus\Http\Cookies\Middleware

#### Classes

| Class                                                                                             | Description |
|---------------------------------------------------------------------------------------------------|-------------|
| [`EncryptCookiesMiddleware`](./Cookies/Middleware/EncryptCookiesMiddleware.md) |             |

### \Qubus\Http\Cookies\Validation

#### Classes

| Class                                                                 | Description |
|-----------------------------------------------------------------------|-------------|
| [`Message`](./Cookies/Validation/Message.md)       |             |
| [`Validation`](./Cookies/Validation/Validation.md) |             |

### \Qubus\Http\Emitter

#### Classes

| Class                                                                    | Description |
|--------------------------------------------------------------------------|-------------|
| [`BaseEmitter`](./Emitter/BaseEmitter.md)             |             |
| [`ContentRange`](./Emitter/ContentRange.md)           |             |
| [`HttpUtil`](./Emitter/HttpUtil.md)                   |             |
| [`SapiEmitter`](./Emitter/SapiEmitter.md)             |             |
| [`SapiStreamEmitter`](./Emitter/SapiStreamEmitter.md) |             |

#### Interfaces

| Interface                                            | Description |
|------------------------------------------------------|-------------|
| [`Emitter`](./Emitter/Emitter.md) |             |

### \Qubus\Http\Emitter\Exceptions

#### Classes

| Class                                                                                                   | Description |
|---------------------------------------------------------------------------------------------------------|-------------|
| [`EmitterException`](./Emitter/Exceptions/EmitterException.md)                       |             |
| [`HeadersAlreadySentException`](./Emitter/Exceptions/HeadersAlreadySentException.md) |             |
| [`PreviousOutputException`](./Emitter/Exceptions/PreviousOutputException.md)         |             |

### \Qubus\Http\Emitter\Middleware

#### Classes

| Class                                                                               | Description |
|-------------------------------------------------------------------------------------|-------------|
| [`EmitterMiddleware`](./Emitter/Middleware/EmitterMiddleware.md) |             |

### \Qubus\Http\Emitter\Traits

#### Traits

| Trait                                                                           | Description |
|---------------------------------------------------------------------------------|-------------|
| [`EmitterTraitAware`](./Emitter/Traits/EmitterTraitAware.md) |             |

### \Qubus\Http\Encryption

#### Interfaces

| Interface                                                     | Description |
|---------------------------------------------------------------|-------------|
| [`Decryptor`](./Encryption/Decryptor.md)   |             |
| [`Encryption`](./Encryption/Encryption.md) |             |
| [`Encryptor`](./Encryption/Encryptor.md)   |             |

### \Qubus\Http\Encryption\Adapter

#### Classes

| Class                                                                           | Description |
|---------------------------------------------------------------------------------|-------------|
| [`QubusEncryption`](./Encryption/Adapter/QubusEncryption.md) |             |

### \Qubus\Http\Encryption\Env

#### Classes

| Class                                                           | Description |
|-----------------------------------------------------------------|-------------|
| [`File`](./Encryption/Env/File.md)           |             |
| [`Parser`](./Encryption/Env/Parser.md)       |             |
| [`SecureEnv`](./Encryption/Env/SecureEnv.md) |             |

### \Qubus\Http\Exception

#### Classes

| Class                                                                              | Description |
|------------------------------------------------------------------------------------|-------------|
| [`MalformedUrlException`](./Exception/MalformedUrlException.md) |             |

### \Qubus\Http\Factories

#### Classes

| Class                                                                                  | Description |
|----------------------------------------------------------------------------------------|-------------|
| [`EmptyResponseFactory`](./Factories/EmptyResponseFactory.md)       |             |
| [`HtmlResponseFactory`](./Factories/HtmlResponseFactory.md)         |             |
| [`JsonResponseFactory`](./Factories/JsonResponseFactory.md)         |             |
| [`Psr17Factory`](./Factories/Psr17Factory.md)                       |             |
| [`RedirectResponseFactory`](./Factories/RedirectResponseFactory.md) |             |
| [`RequestFactory`](./Factories/RequestFactory.md)                   |             |
| [`TextResponseFactory`](./Factories/TextResponseFactory.md)         |             |
| [`XmlResponseFactory`](./Factories/XmlResponseFactory.md)           |             |

### \Qubus\Http\Input

#### Classes

| Class                                              | Description |
|----------------------------------------------------|-------------|
| [`File`](./Input/File.md)       |             |
| [`Handler`](./Input/Handler.md) |             |
| [`Input`](./Input/Input.md)     |             |

#### Interfaces

| Interface                                    | Description |
|----------------------------------------------|-------------|
| [`Item`](./Input/Item.md) |             |

### \Qubus\Http\Session

#### Classes

| Class                                                                  | Description |
|------------------------------------------------------------------------|-------------|
| [`ClientSessionId`](./Session/ClientSessionId.md)   |             |
| [`Flash`](./Session/Flash.md)                       |             |
| [`MessageType`](./Session/MessageType.md)           |             |
| [`NativeSession`](./Session/NativeSession.md)       |             |
| [`SessionData`](./Session/SessionData.md)           |             |
| [`SessionException`](./Session/SessionException.md) |             |
| [`SessionId`](./Session/SessionId.md)               |             |
| [`SessionService`](./Session/SessionService.md)     |             |

#### Traits

| Trait                                                      | Description |
|------------------------------------------------------------|-------------|
| [`FlashAware`](./Session/FlashAware.md) |             |

#### Interfaces

| Interface                                                        | Description |
|------------------------------------------------------------------|-------------|
| [`HttpSession`](./Session/HttpSession.md)     |             |
| [`PhpSession`](./Session/PhpSession.md)       |             |
| [`SessionEntity`](./Session/SessionEntity.md) |             |
| [`Validatable`](./Session/Validatable.md)     |             |

### \Qubus\Http\Session\Middleware

#### Classes

| Class                                                                               | Description |
|-------------------------------------------------------------------------------------|-------------|
| [`SessionMiddleware`](./Session/Middleware/SessionMiddleware.md) |             |

### \Qubus\Http\Session\Storage

#### Classes

| Class                                                                              | Description |
|------------------------------------------------------------------------------------|-------------|
| [`SimpleCacheStorage`](./Session/Storage/SimpleCacheStorage.md) |             |

#### Interfaces

| Interface                                                                  | Description                                                                                       |
|----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| [`SessionStorage`](./Session/Storage/SessionStorage.md) | The Session Storage abstraction defines a
contract for reading/writing/deleting raw Session Data. |

### \Qubus\Http\Swoole

#### Classes

| Class                                                             | Description |
|-------------------------------------------------------------------|-------------|
| [`Request`](./Swoole/Request.md)               |             |
| [`ResponseMerger`](./Swoole/ResponseMerger.md) |             |
| [`ServerRequest`](./Swoole/ServerRequest.md)   |             |

### \Qubus\Http\Swoole\Callback

#### Classes

| Class                                                                                      | Description |
|--------------------------------------------------------------------------------------------|-------------|
| [`CallableRequestHandler`](./Swoole/Callback/CallableRequestHandler.md) |             |
| [`RequestCallback`](./Swoole/Callback/RequestCallback.md)               |             |
| [`RequestCallbackOptions`](./Swoole/Callback/RequestCallbackOptions.md) |             |

### \Qubus\Http\Swoole\Callback\Helpers

#### Helpers

| Function                                              | Description |
|-------------------------------------------------------|-------------|
| [`request_callback()`](./Helpers/request_callback.md) |             |

### \Qubus\Http\Swoole\Factory

#### Classes

| Class                                                                     | Description |
|---------------------------------------------------------------------------|-------------|
| [`RequestFactory`](./Swoole/Factory/RequestFactory.md) |             |

#### Interfaces

| Interface                                                                     | Description |
|-------------------------------------------------------------------------------|-------------|
| [`PsrSwooleFactory`](./Swoole/Factory/PsrSwooleFactory.md) |             |
