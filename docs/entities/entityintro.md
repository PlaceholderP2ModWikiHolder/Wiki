# Intro To Entities
PlaceholderMod allows the creation of [Entities](https://developer.valvesoftware.com/wiki/Entity) through C# Scripting. To define an Entity, you need to inherit from BaseEntity and override `OnStart()` and `OnUpdate()` methods for all logic.

```CSharp
public class MyEntity : BaseEntity
{
    // This will run once on Start
    public override void Start()
    {
        Console.WriteLine("Starting MyEntity...");
    }

    // This will run once per frame
    public override void Update()
    {
        Console.WriteLine("Updating MyEntity!");
    }
}
```

## Exposing Entity Variables to the Editor
To expose an Entity Variable to the Editor, you can utilize the `[EntityProperty]` Attribute. Any Variables marked with this Attribute will be accessible and editable directly from the Editor.

```CSharp
[EntityProperty("light_color")]
public Vector4 Color = new Vector4(255.0f, 255.0f, 255.0f, 200.0f);
```

!!! warning
    Entity Properties only support the Datatypes that the [KeyValues](../../fileformats/keyvalues) format supports.

## Entity Deletion
Entities can be deleted through the `Entity.DestroyDeferred()` method. This method will clean up the Entities with their `OnDestroy()` method before deleting it from the world.

```CSharp
// Run any Entity clean-up and then remove it from the World
EntityReference.DestroyDeferred();
```

## Entity Types
Entities come in 2 primary types, Point Entities and Brush Entities.

### Point Entity
A Point Entity is an Entity that occupies a single point in the world.

```CSharp
public class PropEntity : MeshEntity
{
    /// <summary>
    /// Create Mesh from this path.
    /// </summary>
    [EntityProperty("model")]
    public string MeshPath;

    /// <summary>
    /// Get Material from this path.
    /// </summary>
    [EntityProperty("skin")]
    public string MaterialPath;

    public override void Start()
    {
        Material material = FileSystem.GetMaterial(MaterialPath);
        Mesh = new Mesh(FileSystem.GetModelPath(MeshPath), material);

        GameWindow.CurrentWindow.Renderer.InitMesh(Mesh); // Render the (empty) mesh
    }
}
```

### Brush Entity
A Brush Entity is an Entity that occupies Map Geometry (Brushes).