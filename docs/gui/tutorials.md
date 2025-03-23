# Tutorials


## Creating a Screenspace GUI Entity
In this tutorial, we'll create an Entity that renders a VistaGUI Canvas to the screen when placed in a Map and add a button to generate a random number, all written in C#.

To get started, create a new blank Entity in your project that inherits from `ScreenspaceGUICanvas` and implements the `Start()` method. This file can have any name, but for this Tutorial we will be naming it `MyScreenspaceCanvas.cs`.

```CSharp
public class MyScreenspaceCanvas : ScreenspaceGUICanvas
{
	// This function will run once on start.
	public override void Start()
	{

	}
}
```

Now we have an empty GUI Entity that we can use in-game, but we haven't created a GUI to render yet. Let's make a new `.html` file inside our game's `gui` folder. For this tutorial, we'll name the file `my-screenspace.html`.

Next, we can open this file and define some Elements to render. VistaGUI HTML consists of a `<head>` section and a `<body>` section. The `<body>` contains all the visible Elements in the Canvas, while the `<head>` contains things like CSS styling and meta-data.

```HTML
<head>
	<!-- We don't have any styling, so we leave the head empty. -->
</head>

<body>
	<button>Click Me!</button>
</body>
```

This will add a single Button with the text "Click Me!" inside. Now, let's tell our Entity that we want to render this file.

```CSharp
public class MyScreenspaceCanvas : ScreenspaceGUICanvas
{
	// This function will run once on start.
	public override void Start()
	{
		// Let the Entity know which .html file to render
		PanelName = "my-screenspace.html"; 
	}
}
```

Now we have an Entity linked to a valid Vista HTML file, but if you try to use it you'll notice that nothing renders. This is because we need to tell the Entity to start the GUI once it's configured.

We can do this in the `Start()` method by using `base.Start();` like so:

```CSharp
public class MyScreenspaceCanvas : ScreenspaceGUICanvas
{
	// This function will run once on start.
	public override void Start()
	{
		// Let the Entity know which .html file to render
		PanelName = "my-screenspace.html";

		// Start the GUI
		base.Start();
	}
}
```

Now that we have a Canvas rendering to the screen with a button inside, let's add some functionality and allow it to generate a random number when pressed.

### Functionality
VistaGUI can interact with the front-end within the C# API via the [Events](../events) System. In this tutorial, we'll be using C# exclusively. However, VistaGUI also supports JavaScript and recommends using it for code that isn't engine-dependent. For more information on the relationship between JavaScript and C#, refer to the [Intro to VistaGUI](../intro) page.

Let's get started by triggering an event inside our previously created `.html` file using our buttons `onclick` attribute.

```HTML
<head>
	<!-- We don't have any styling, so we leave the head empty. -->
</head>

<body>
	<button onclick="GenerateNumber()">Click Me!</button>
</body>
```

Now, let's register some code to run when our `GenerateNumber` event gets triggered inside our Entity using `RegisterEvent`.

```CSharp
public class MyScreenspaceCanvas : ScreenspaceGUICanvas
{
	// This function will run once on start.
	public override void Start()
	{
		// Let the Entity know which .html file to render
		PanelName = "my-screenspace.html";

		// Start the GUI
		base.Start();


		// Register the "GenerateNumber" Event
		RegisterEvent("GenerateNumber", GenerateNumber());
		void GenerateNumber()
		{
			Console.WriteLine("Pressed Button!");
		}
	}
}
```

!!! tip
	`RegisterEvent()` Will run any [Action](https://learn.microsoft.com/en-us/dotnet/api/system.action?view=net-9.0), it doesn't have to be a defined function.

Clicking our Button will now log "Pressed Button!" to the Console. Let's add another level of interaction by making our button affect a Text element in our GUI.

We'll start by adding another Element to our `.html` file.

```HTML
<head>
	<!-- We don't have any styling, so we leave the head empty. -->
</head>

<body>
	<p>My Text</p>
	<button onclick="GenerateNumber()">Click Me!</button>
</body>
```

Now we have a `<p>` Element rendering 'My Text' in our GUI. Let's expose this to our Entity code by using an `id` attribute.

```HTML
<head>
	<!-- We don't have any styling, so we leave the head empty. -->
</head>

<body>
	<p id="my-text-element">My Text</p>
	<button onclick="GenerateNumber()">Click Me!</button>
</body>
```

We can now get a reference to this Element inside our Entity with the following code:

```CSharp
public class MyScreenspaceCanvas : ScreenspaceGUICanvas
{
	// This function will run once on start.
	public override void Start()
	{
		// Let the Entity know which .html file to render
		PanelName = "my-screenspace.html";

		// Start the GUI
		base.Start();


		// Register the "GenerateNumber" Event
		RegisterEvent("GenerateNumber", GenerateNumber());
		void GenerateNumber()
		{
			// Get our Text Element
			VistaText myTextElement = Canvas.GetElementAsType<VistaText>("my-text-element");
		}
	}
}
```

Let's finish our Entity by generating a random number and setting our Elements Text using `myTextElement.TextContent = "Text Goes Here"`.

```CSharp
public class MyScreenspaceCanvas : ScreenspaceGUICanvas
{
	// This function will run once on start.
	public override void Start()
	{
		// Let the Entity know which .html file to render
		PanelName = "my-screenspace.html";

		// Start the GUI
		base.Start();


		// Register the "GenerateNumber" Event
		RegisterEvent("GenerateNumber", GenerateNumber());
		void GenerateNumber()
		{
			// Get our Text Element
			VistaText myTextElement = Canvas.GetElementAsType<VistaText>("my-text-element");

			// Generate a random number (0-100)
			Random random = new Random();
			int randomNumber = random.Next(0, 101);

			// Set our Text to the number
			myTextElement.TextContent = randomNumber.ToString();
		}
	}
}
```

Congratulations! You should now have a functional random number generator using VistaGUI.