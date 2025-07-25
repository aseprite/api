# NewFile

```lua
app.command.NewFile {
  ui=bool,
  width=int,
  height=int,
  colorMode=ColorMode,
  fromClipboard=bool
}
```

* `ui`: Shows the new file dialog, defaults to `true`.
* `width`: The width of the new sprite, ignored when using `fromClipboard`.
* `height`: The height of the new sprite, ignored when using `fromClipboard`.
* `colorMode` ([ColorMode](../colormode.md#colormode))
* `fromClipboard`: Use the current clipboard to create the file.
