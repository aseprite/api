# LoadPalette

```lua
app.command.LoadPalette {
  ui=bool,
  filename=string
  preset=string
}
```

Loads a palette from the given `preset` or `filename`.

* `ui`: Shows the file picker dialog with `filename` pre-completed, `true` by default. Set to
  `false` to load `filename` directly without user confirmation.
* `filename`: A path to a supported palette or file to extract a palette from, optional.
* `preset`: The name of a palette preset, `"default"` resets the palette to default. If set, `filename` is ignored.

