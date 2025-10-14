***

# EntityRepository





* Full name: `\Codefy\Domain\Model\EntityRepository`



## Methods


### findEntityById

Find an Entity by its id.

```php
public findEntityById(\Codefy\Domain\Model\EntityId $entityId): \Codefy\Domain\Model\Entity|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$entityId` | **\Codefy\Domain\Model\EntityId** | Entity id. |


**Return Value:**

Returns Entity object if existed, null otherwise.



**Throws:**
<p>The ID of this entity is invalid.</p>

- [`EntityNotFoundException`](./EntityNotFoundException.md)



***

### saveEntity

Save an Entity.

```php
public saveEntity(\Codefy\Domain\Model\Entity $entity): \Codefy\Domain\Model\EntityId|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$entity` | **\Codefy\Domain\Model\Entity** |  |


**Return Value:**

If saved successfully, return EntityId, null otherwise.




***


***
> Automatically generated on 2025-10-13
