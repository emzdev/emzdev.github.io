# Routing gamepad input to focused Standalone Game Window

The default behaviour of a PIE Standalone Game is to route inputs to all PIE sessions even when the window is not focused. 
This is especially problematic when you're dealing with multiple PIE windows (while testing out online features for instance) 
but you only want to route controller inputs to one window at a time.

There is a CVar you can enable to only route gamepad input to the focused window:
``` cpp
Slate.RequireFocusForGamepadInput 1
```
