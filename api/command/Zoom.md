# Zoom

```lua
app.command.Zoom {
  action=string,
  percentage=int,
  focus=string
}
```

Performs a zoom on the active editor.

* `action`: One of `"in"`, `"out"`, or "`set`"
* `percentage`: The amount to set the zoom to (ignores `action`)
* `focus`: From where we are doing the zoom, can be `center` or `mouse`