# SetLoopSection

```lua
app.command.SetLoopSection {
  action=string,
  begin=int,
  `end`=int,
}
```

Set the looping property of the given frame range.

* `action`: The action to take. `"auto"` derives it from the selected range and ignores the `begin` and `end` parameters, `"on"` creates the looping section and `"off"` removes it.
* `begin`: The start of the frame range to change
* `end`: The end of the frame range.

