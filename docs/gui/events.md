# Events
An Event is a function that is triggered from HTML or JavaScript and then executes code via the C# API.

Calling an Event is just like calling a JavaScript function, for example, using `onclick="EventName()"` inside a button will call the 'EventName()' Event assuming the function isn't already defined inside JavaScript.

Registering an Event inside C# is done by running `RegisterEvent("EventName", Action);` on a GUICanvas entity. This will trigger the specified Action when 'EventName()' is called.

## Unregistering Events
Events should be unregistered when the associated entity is destroyed, you can unregister events through `UnregisterEvent("EventName")` in the `OnDestroy()` method.

## Examples

**Setting Text with an Event**
```HTML
<button onclick="SetText()">Set Text</button>
<p id="text-label">Original Text</p>
```

```CSharp
// Sets Text of a Text-Based Element when "SetText()" Event is called from JS.
RegisterEvent("SetText", () => SetText());
void SetText()
{
    // Set Text
    VistaText textElement = GetElementAsType<VistaText>("text-label");
    textElement.TextContent = "Set Text Content!";
}
```