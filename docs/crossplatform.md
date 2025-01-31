# crossplatform

## `:currentInputType(differentiateGamepads: boolean)`

Returns a string of the last input type, either Keyboard, Touch or Gamepad.  If `differentiateGamepads` is `true`, it will return `"PS"` and `"Xbox"` depending on which gamepad is being used, if any.

## `:templateString(stringTemplate : string, inputMap)`

Returns a string formatted using the current input type and the provided InputMap.

## `:mapStrings(inputMap)`

Returns a string from the InputMap for the current input, if one exists.

## `:mapImages(inputMap)`

Returns an image from an InputMap for the current input, if one exists.

## `:registerObject(object : any, inputMap, stringTemplate : string?)`

Binds an object to update when the control method is changed. If a stringTemplate is not provided, it will be replaced with `"%s"`.

