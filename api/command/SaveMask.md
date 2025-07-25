# SaveMask

```lua
app.command.SaveMask {
  ui=bool,
  filename=string
}
```

Saves the current selection mask to a *.msk file.

* `ui`: Shows the file picker dialog with `filename` pre-completed, `true` by default. Set to
  `false` to save `filename` directly without user confirmation.
* `filename`: A path to a *.msk file or a path to pre-load into the file picker dialog. Defaults to `default.msk`.

