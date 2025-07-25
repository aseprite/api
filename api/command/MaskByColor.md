# MaskByColor

```lua
app.command.MaskByColor {
  ui=bool,
  color=Color,
  tolerance=int,
  mode=SelectionMode
}
```

Creates a new selection by color

* `ui`: Shows the dialog on the screen, `true` by default. Set to `false` to select automatically.
* `color`: The [color](../color.md#color) to mask by. Defaults to the current foreground color.
* `tolerance`: The maximum allowed difference between `color` and the pixel to be selected, from `0` to `255`. Defaults to `0`
* `mode`: [SelectionMode](../selectionmode.md)
