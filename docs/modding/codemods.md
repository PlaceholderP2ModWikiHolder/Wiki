# Code Mods
Code Mods are mods that interface with the C# API to introduce new features, usually in the form of Entities or something similar. They are highly versatile, both the Game code and the Editor code are Code Mods.

## Creating a Code Mod
To create a Code Mod, place a `.dll` file linked to `Engine.dll` inside the `bin/mods` folder. By default, all Entities defined in the mod's `.dll` will be usable in-game automatically.

## Mod Entry-Points
Mods can optionally define an "Entry-Point" which allows the Mod to automatically run code when it is loaded or unloaded by the engine. To add an Entry-Point to your Mod, create a class that inherits from the `IMod` interface and implement both the `OnLoad()` and `OnUnload()` methods.

``` CSharp
// Entry-Point for 'MyMod'
public class MyMod : IMod
{
    // Runs once on Mod Load
    public void OnLoad()
    {

    }

    // Runs once on Mod Unload
    public void OnUnload()
    {

    }
}
```

A Mod can have any number of Entry-Points, but for the sake of convenience and organization, it's recommended to have only one.

## Mod Clean Up
Each Mod should ideally manage itself through it's Entry-Point's `OnLoad()` and `OnUnload()` methods, if applicable. This means any actions performed by the Mod during loading should be undone when the Mod is unloaded. For example, if a GameObject is created in `OnLoad()`, it should be destroyed in `OnUnload()`.