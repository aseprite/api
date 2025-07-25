# SavePalette

```lua
app.command.SavePalette {
  ui=bool,
  filename=string,
  preset=string,
  saveAsPreset=bool,
  columns=int
}
```

Saves the current palette to a file or the given preset.

* `ui`: Shows the file picker dialog, `true` by default.
* `filename`: A path to where to save the palette. Optional and ignored if `saveAsPreset` is `true`.
* `preset`: The preset to save to. Optional.
* `saveAsPreset`: Whether to save to the preset or the file, defaults to
* `columns`: Defaults to `16`.

