# GameInfo
PlaceholderMod, like Source Engine mods, includes a `gameinfo.txt` file in its root Game directory. During development you may need to access the contents stored in the `gameinfo.txt` file through the C# API.

## Accessing GameInfo.txt
The game's `gameinfo.txt` can be accessed through the GameInfo class. Since `gameinfo.txt` uses the [KeyValues](../../fileformats/keyvalues) format, the class provides standard functions for collecting data from KeyValues, along with gameinfo-specific functions.

## Game Specific Data
| Function    | Data | GameInfo Definition|
| -------- | ------- | ------- |
| GetGameName()  | Game Name/Title. | Defined in the `game` KeyValue |
| GetSteamAppID() | Steam App ID of the Mounted Game. | Defined in the `SteamAppId` KeyValue     |
| GetMountedPaths()    | Path of all Mounted Games. |  Defined in the `Game` KeyValue(s) |