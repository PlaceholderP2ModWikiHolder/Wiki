# Intro To Modding
By default, PlaceholderMod ships with enhanced modding support for both Content and Code mods. While mods cannot modify existing engine code, they can extend it by adding features like scripted Entities.

Mods are highly versatile and capable. For instance, the Editor itself is an Engine Mod.

## Content Mods
Content Mods are similar to typical Portal 2 Mods, adding things like Maps, Models, Materials, etc., but they don't alter or extend the underlying code.

Note: Full support for Content Mods is still in development. For now, you can simply replace/add to files.

## Code Mods
Code Mods differ from Content Mods in that they introduce custom features defined through code. These mods compile to a `.dll` file and are loaded by the Engine during runtime.

## Total-Conversion Mods
When Content Mods and Code Mods are combined on a high level, they form a Total-Conversion mod. These mods can function as standalone games with their own executables and binaries and in some cases not requiring PlaceholdeeMod to be installed at all.