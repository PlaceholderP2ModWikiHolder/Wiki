# Render Passes
PlaceholderMod handles Rendering of different object types through a "Render Pass" system.

## Built-In Render Passes

| Render Pass         | Purpose                                                   |
|---------------------|-----------------------------------------------------------|
| **Mesh Entity Pass**    | Renders all Mesh Entities. |
| **Screenspace GUI Pass**    | Renders all Screenspace GUIs to the screen. |

## Defining a Custom Render Pass
Code Mods allow you to define custom Render Passes via their Entry-Point. To create a new Render Pass, define a class that inherits from `BaseRenderPass`, and then register it in your Mod's Entry-Point using `RenderPassManager.RegisterPass(new PassClassName());`

*Render Pass Definition:*
```CSharp
public class ScreenspaceGUIPass : BaseRenderPass
{
    // Enable Blending
    public override List<RenderFlag> RenderPassFlags => new List<RenderFlag> { RenderFlag.Blend };

    // Run RenderEntity on render
    public override void OnRender() => RenderEntities<GUICanvasEntity>(EntityManager.Root);

    // Render Screenspace GUIs
    protected override void RenderEntity<TEntity>(TEntity entity)
    {
        if (entity is GUICanvasEntity guiEntity)
        {
            Renderer.RenderScreenspaceGUI(guiEntity);
        }
    }
}
```

*Render Pass Registry:*
```CSharp
// Entry-Point for MyMod
public class MyMod : IMod
{
    // Runs once on Mod Load
    public void OnLoad()
    {
        RenderPassManager.RegisterPass(new ScreenspaceGUIRenderPass()); // Register Screenspace GUI Render Pass
    }
}
```
