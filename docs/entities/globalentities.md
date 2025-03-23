# Global Entities
Global Entities are Entities that maintain a persistent state across maps. When a map is unloaded, Global Entities remain intact. The `Start()` method of a Global Entity is executed once upon game launch.

## Creating Global Entities
To create a Global Entity in C#, you can use the `EntityManager.AddGlobalEntity()` method.

```CSharp
BaseEntity myEntity = new BaseEntity();
EntityManager.AddGlobalEntity(myEntity);
```