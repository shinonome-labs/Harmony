# Quickstart

Harmony is a library meant to supplement your UI and help out with `ContextActionService`.

The basis of Harmony is an InputMap, which looks like this:

```lua
local inputMap = {
	Action = {
		Name = "Activate",
		Type = "PressOnce"
	},
	Keyboard = {
		Button = Enum.KeyCode.E,
		Image = "KEYBOARD_IMAGE"
	},
	Activated = function()
		print("Activated!")
	end,
}
```

Harmony uses this InputMap for several different actions. These define the entire basis of what a certain input means to Harmony and your UI.

In this example, we use `Harmony.crossplatform` to bind a ImageLabel and TextLabel to update with our InputMap, and use `Harmony.actions` to wrap `ContextActionService` for our input:

```lua
    -- Assuming this is a script inside a ScreenGui with a ImageLabel and TextLabel, using the InputMap above
    local Harmony = require(game.ReplicatedStorage.Harmony)
    
    Harmony.crossplatform:registerObject(script.Parent.TextLabel,
	inputMap,
	"Press %s to activate")

    Harmony.crossplatform:registerObject(script.Parent.ImageLabel,
	inputMap)

    Harmony.actions:wrap(inputMap)
    
```

https://github.com/user-attachments/assets/89c924d4-a307-4d70-982b-c73cd865fe53

Awesome! Harmony correctly changes our TextLabel and ImageLabel to what the InputMap specfies, and logs "Activated!" to the console when we press E.

In this example, Harmony's crossplatform functionality isn't being taken advantage of yet. We can add cross platform prompt support by expanding our InputMap to include the `Touch` and `Gamepad` control schemes:

```lua
local inputMap = {
	Action = {
		Name = "Activate",
		Type = "PressOnce"
	},
	Keyboard = {
		Button = Enum.KeyCode.E,
		Image = "KEYBOARD_IMAGE"
	},
	Gamepad = {
		Button = Enum.KeyCode.ButtonY,
		Image = {
			Xbox = "XBOX_IMAGE",
			PS = "PS_IMAGE"
		}
	},
	Touch = {
		Button = "Activate",
		Image = "TOUCH_IMAGE",
		TouchButton = { -- This section defines how ContextActionService should reposition and resize our button for touch support
			Position = UDim2.new(0.5, 0, 0.5, 0),
			Size = UDim2.new(0, 50, 0, 50),
			Image = "BUTTON_IMAGE"
		}
	},
	Activated = function()
		print("Activated!")
	end,
}

Harmony.crossplatform:registerObject(script.Parent.TextLabel,
inputMap,
"Press %s to activate")

Harmony.crossplatform:registerObject(script.Parent.ImageLabel,
inputMap)

Harmony.actions:wrap(inputMap)
```

Now when we play our game, touchscreens and controllers update our UI accordingly and the inputs we defined in the InputMap work!


https://github.com/user-attachments/assets/cb9344d6-6c37-4a57-9f6d-563e12474604



`Action.Type` can be changed to any of the following to suit your needs:
- `"PressOnce"`: Fires once when the input is triggered
- `"Hold"`: Fires twice, once when the input is triggered and once when it is released. Passes the `Activated` function a bool representing if the input is being held
- `"Raw"`: Passes through the underlying `ContextActionService` data to `Activated`

For more information on Harmony APIs, please see the rest of this docs directory.
