# OpenFile

```lua
app.command.OpenFile {
  ui=bool,
  filename=string,
  folder=string,
  repeat_checkbox=bool,
  oneframe=bool,
  sequence=string
}
```

Opens a file, or sequence of files (UI only through the dialog)

* `ui`: Shows the file opening dialog, `true` by default.
* `filename`: The filename to open
* `folder`: Folder to pre-fill the dialog (with UI only)
* `repeat_checkbox`: Whether the file renaming actions for sequences will show a dialogue or use the given `sequence` (UI only)
* `sequence`: One of `"ask"`, `"yes"`, or `"no"`.
