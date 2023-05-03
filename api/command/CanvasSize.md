# CanvasSize

```lua
app.command.CanvasSize {
  ui=true,
  left=0,
  top=0,
  right=0,
  bottom=0,
  bounds=Rectangle,
  trimOutside=false
}
```

* `ui`: `false` if you don't need to show the dialog to the user.
* `left`/`top`/`right`/`bottom`: How many pixels to add, or remove if
  the value is negative, to/from left/top/right/bottom sides.
* `bounds`: A new [rectangle](../rectangle.md#rectangle) with the new
  bounds of the canvas. If you use this argument,
  `left/top/right/bottom` are ignored.
* `trimOutside`: True if you want to delete all the pixel content of
  cels that will be outside the canvas after the canvas size is
  modified.

Examples. Add 8 pixels at the left side:

```lua
app.command.CanvasSize { ui=false, left=8 }
```

Add 8 pixels to the left and 8 pixels to the right (new width = old
width + 16 pixels):

```lua
local r = app.sprite.bounds
r.x = r.x-8
r.width = r.width+16
app.command.CanvasSize { ui=false, bounds=r }
```
