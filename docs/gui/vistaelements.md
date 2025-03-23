# Vista Elements
PlaceholderMod ships with custom VistaGUI Elements designed to simplify the process of developing Game GUIs. Below is a list of all custom Elements along with their respective `.js` file.

| Element | Purpose  |`.js` File |
|----------|----------|----------|
| `<vista-panel>`   | A Draggable Panel | `panels.js` |

## Using Vista Elements
To use a Vista Element in your HTML, include the appropriate `.js` file from `gui/elements` and then treat it like any other HTML Element. For example, to use `<vista-panel>` add the following line to your file's `<head>`: `<script src="file:///elements/panels.js"></script>` and then you can add it to the page like so:
```HTML
<vista-panel>
    <p>My Vista Panel</p>
</vista-panel>
```
