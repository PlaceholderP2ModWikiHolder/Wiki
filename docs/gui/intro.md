# Intro to VistaGUI
VistaGUI is the complete replacement for Source Engine's GUI System, phasing out the outdated [VGUI](https://developer.valvesoftware.com/wiki/VGUI_Documentation). VistaGUI is more similar in workflow to Valve's newer GUI System, [Panorama](https://developer.valvesoftware.com/wiki/Panorama), by heavily utilizing Web Development techniques.

## Front-End
A VistaGUI Frontend is built using standard Web Development tools like HTML, CSS and optionally JavaScript. Unlike typical HTML, however, it doesn't require defining metadata or specifying itself as HTML.

## Back-End (Engine Interaction)
When building a GUI, it will eventually need to integrate with the Engine. In Vista, this is done through [Events](../events). An Event is triggered from HTML or JavaScript and then executes code via the C# API.

## Combining JavaScript and C\#
With the option of two seperate scripting languages, it can be difficult to determine when to use each one. Generally, JavaScript should be used for all functionality that doesn't require Engine interaction, while C# should be used for anything that involves Engine interaction.

Using JavaScript for Front-End isn't a necessity as C# can be used for functionality typically handled by JavaScript. However, JavaScript has no access to the Scripting API and cannot manipulate the Engine alone.
