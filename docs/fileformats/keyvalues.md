# KeyValues File Format
During Mod development, you might need to store data in an easy-to-use text format. For this purpose, we use Valve's [KeyValues](https://developer.valvesoftware.com/wiki/KeyValues) format.

## Parent Keys
Parent Keys contain Nested Parent Keys and Key Values. They are defined by a name, followed by an opening curly brace `{`, the contents of the Parent Key, and a closing curly brace `}`.

```KeyValues
Name 
{
    any other parent keys or key values would go here.
}
```

## Key Values
Key Values contain accessible variable data in text form. They are defined by a Key (Name), followed by an indent and the desired Value.

```KeyValues
Name    "Value"
```

### Supported Value Datatypes
| Type   | Formatting Example  |
|--------|----------|
| Integer | "123" |
| Float | "123.1" |
| Boolean | "true" |
| String  | "string" |
| Vector3  | "(1 2 3)" *OR* "1 2 3" |
| Vector4  | "(1 2 3 4)" *OR* "1 2 3 4" |

## C# API
The KeyValues Format can be parsed through the KeyValuesFormat Class. This Class breaks a KeyValues file into the following structure.

```KeyValues
ParentKey
├── ChildParentKey
│   ├── ChildKeyValue
│   └── ChildKeyValue
└── ChildKeyValue
```

To parse a KeyValue file using the C# API, first read the file contents, then create a new instance of the `KeyValuesFormat` class like this:
`new KeyValuesFormat(file_contents)`



### GameInfo Example
The following is an example of parsing a KeyValues file and getting Values from it to parse GameInfo.txt:
```CSharp
    /// <summary>
    /// Holds data from gameinfo.txt.
    /// </summary>
    public class GameInfoFormat
    {
        public KeyValuesFormat KeyValues;
        
        // Data
        public string GameName;
        public int SteamAppID;

        public GameInfoFormat(string content)
        {
            // Load KeyValues
            KeyValues = new KeyValuesFormat(content);

            // Populate Data
            GameName = (string) KeyValues.GetKeyValue("game").Value;
            SteamAppID = (int) KeyValues.GetKeyValue("SteamAppId").Value;
        }
    }
```