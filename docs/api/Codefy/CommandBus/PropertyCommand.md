# PropertyCommand

Abstract class for constructing property mappings.

Example:
final class CreatePostCommand extends PropertyCommand
{
    public PostId $postId;
}

$command = new CreatePostCommand(['postId' => new PostId()]);
$odin->execute($command);

***

* Full name: `\Codefy\CommandBus\PropertyCommand`
* This class implements:
  [`\Codefy\CommandBus\Command`](./Command.md)
* This class is an **Abstract class**

## Methods

### __construct

```php
public __construct(array $data = []): mixed
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

**Throws:**

- [`CommandPropertyNotFoundException`](./Exceptions/CommandPropertyNotFoundException.md)

***
