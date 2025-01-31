# settings

This module provides a table defining how Harmony should behave. Currently, there's only one option you can change:

## State
Controls behavior of Harmony's state
### Error
Choose what Harmony should do when an object in the state fails to update

true: Throw an error and halt the state update
false: Throw a warning about the offending object, remove it from the state and continue updating

Production: `true`
Studio: `false`