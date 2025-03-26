# Entity Inputs and Outputs
The C# API provides easy-to-use methods of integrating an Entity into the [Map I/O System](https://developer.valvesoftware.com/wiki/Inputs_and_Outputs).

## Defining an Input
Inputs can be defined by applying the `[Input]` attribute to a method. Any method with this attribute will automatically be callable through Map Logic.

```CSharp
[Entity("my_entity")]
public class MyEntity : BaseEntity
{
    [Input]
    public void PrintConsoleMessage()
    {
        DeveloperConsole.Msg("Input was ran!");
    }

}
```

## Firing an Output
Outputs can be triggered using the `FireOutput()` method, which will fire all outputs connected to the provided name parameter.

```CSharp
[Entity("my_entity")]
public class MyEntity : BaseEntity
{
    public override void Start()
    {
        FireOutput("Started");
    }
}
```