# LoadMask

```lua
app.command.LoadMask {
  ui=bool,
  filename=string
}
```

Loads a mask from the given *.msk file.

* `ui`: Shows the file picker dialog with `filename` pre-completed, `true` by default. Set to
  `false` to load `filename` directly without user confirmation.
* `filename`: A path to a *.msk file or a path to pre-load into the file picker dialog.
