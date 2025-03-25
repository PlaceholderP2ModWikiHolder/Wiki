# Developer Console
The C# API Provides easy-to-use methods of interacting with the [Developer Console](https://developer.valvesoftware.com/wiki/Developer_console).

## Logging to the Console
The Console can be written to via the `DeveloperConsole` class. This class provides three Logging methods: `Msg()`, which logs a simple white message; `Warning()`, which logs a yellow message; and `Error()` which logs a red message.

```CSharp
DeveloperConsole.Msg("White Logging Message");
DeveloperConsole.Warning("Yellow Warning Message");
DeveloperConsole.Error("Red Error Message");
```

## Console Commands
Registering a ConCommand can be done through applying the `[ConCommand]` attribute to a static method.

```CSharp
[ConCommand("my_command")]
static void MyCommand()
{
    DeveloperConsole.Msg("Hello World!");
}
```

!!! warning
    Console Commands will only work on `static` methods.

## Console Variables
Registering a ConVar can be done through applying the [ConVar] attribute to a static property.

```CSharp
[ConVar("my_convar")]
public static string MyConvar { get; set; } = "My Awesome Convar";
```

!!! warning
    Console Variables will only work on `static` properties.

### Flags
Console Variables support unique behaviour through the `ConVarFlag` enum. To apply a flag, include it in the `ConVar` constructor like so:

```CSharp
// Create a ConVar with the 'Save' Flag
[ConVar("my_convar", ConVarFlag.Save)]
public static string MyConvar { get; set; } = "My Awesome Convar";
```

| Flag     | Purpose     |
|--------------|--------------|
| **Save** | Enables the ConVar's value to persist between games. |
