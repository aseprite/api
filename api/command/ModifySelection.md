# ModifySelection

```lua
app.command.ModifySelection {
  ui=bool,
  modifier=string,
  quantity=int,
  brush=string
}
```

Modifies the active selection.

* `ui`: Shows the selection modification dialog on screen, `true` by default. Set to `false` to modify automatically.
* `modifier`: One of `"border"`, `"expand"`, or `"contract"`.
* `quantity`: The pixel amount to modify the selection by. *Note*: Will attempt to show the UI if set to `0`.
* `brush`: One of `"circle"`, or `"square"`.
