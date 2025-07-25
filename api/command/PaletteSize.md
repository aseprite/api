# PaletteSize

```lua
app.command.PaletteSize {
  ui=bool,
  size=int
}
```

Changes the palette size

* `ui`: Shows the palette resizing dialog, defaults to `true`.
* `size`: The new palette size. *Note*: Will attempt to show the UI if set to `0`.