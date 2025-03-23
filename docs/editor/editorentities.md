# Editor Entities
When expanding the Editor, you may want to create an Entity that can run code in the Editor. To do this, you can use the `[AlwaysExecute]` Attribute on the Entity class.

This Example will print "Editor Update logic" once per update in the Editor.
```CSharp
[AlwaysExecute]
public class MyEditorEntity : BaseEntity
{
    public override void Update() 
    {
        Console.Log("Editor Update logic");
    }
}
```
!!! note
    `[AlwaysExecute]` Will run Entity logic both In-Editor and In-Game.