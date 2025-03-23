# Gizmos
When creating an Entity you may want to assign a custom Editor Gizmo. This can be acheived by overriding the `DrawGizmos()` and `DrawGizmosSelected()` functions of the Entity respectively.

!!! note
    To prevent Gizmo-related code from being included in the shipped game when not in use, wrap these functions in a `#if EDITOR` directive.

## Rendering Primitives
The `Gizmos` class offers features for rendering different types of Primitives within your Gizmos. To set the Color of a Primitive you can set `Gizmos.Color` before rendering the Primitive.

```CSharp
#if EDITOR
public override void DrawGizmos()
{
    // Draw a Red Cube sized at 32 units at the Entity position
    Gizmos.Color = new Vector4(255, 0, 0, 1);
    Gizmos.DrawCube(Transform.Position, new Vector3(32.0f, 32.0f, 32.0f));
}
#endif
```

!!! warning
    Gizmo Primitives are not parented to the Entity by default.