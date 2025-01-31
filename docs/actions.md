# actions

## `:wrap(inputMap)`

Use an InputMap to make a ContextActionService bind, additionally provides abstractions for things like key holding and press once actions.

## `:unbind(inputMap)`

Equivalent to ContextActionService:Unbind(), but the relevant action is also removed from the internal map to stop a memory leak

## `.eventHandler(actionName, inputState, inputObject)`

Provides the abstractions as described in :wrap()