# Element Manipulation
The C# API provides many methods of manipulating Elements on the Front-End from code.

## Getting an Element
A C# reference to an Element can be obtained using `GetElementAsType<ElementType>(ElementID)`. However, not every front-end element has a direct C# equivalent. In cases like this, you can use the generic `VistaElement` Type as an alternative.

Some Elements don't have a direct C# equivalent but instead have a more general Type. For instance, **all** Text Elements use the `VistaText` Type.

## Modifying an Element
Element references offer various functions for changing properties, HTML, style, and more. Each Element Type has it's own specific methods for changing content related to that Type. For example, `VistaImage` has an 'ImageSource' variable that determines the file path for the image, while `VistaText` has a 'TextContent' variable that controls the Text inside the Element. However, there are generic methods that all Elements share.

| Function    | Purpose |
| -------- | ------- |
| SetInnerHTML(html)  | Sets the `InnerHTML` Property of the Element.    |
| SetProperty(property, value) | Sets a Property of the Element.     |
| SetStyle(style)    | Sets the Style (CSS) of the Element.    |

These generic functions typically have a corresponding 'Get' version that retrieves the value instead of setting it. For example, `GetStyle()` will return the Elements CSS.

## Examples

**Changing Image Source via VistaElement and VistaImage**
```CSharp
// Change the Image Source of a generic VistaElement.
VistaElement imageElement = GetElementAsType<VistaElement>("image");
imageElement.SetProperty("src", "file:///images/test_image.png");
```

```CSharp
// Change the Image Source of a VistaImage
VistaImage imageElement = GetElementAsType<VistaImage>("image");
imageElement.ImageSource = "file:///images/test_image.png";
```