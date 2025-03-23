# Working With Files
PlaceholderMod uses a unique file structure, utilising features such as mounted game support. The C# API provides comprehensive functionality for managing and working with files across game-specific and mounted folders and packages.

## Getting an Asset Path
Each asset type has an associated FileSystem function to get its path. For example, `GetMaterialPath("metal/material_name")` will return the path to a `.vmt` file called 'material_name' inside 'materials/metal'.

## Getting an Asset
Some asset types support directly retrieving their type through a FileSystem function. For example, `GetMaterial("material_name")` will return the Material object for 'material_name'.

## Asset Search Paths
When getting an Asset by its path or reference, the File System will first search the Game directory. If it fails to find the Asset in the Game directory, it will then search mounted Game directories. This causes local Game Assets to always take priority over mounted Game Assets.