# ChangeBrush

```lua
app.command.ChangeBrush {
    change=string
    slot=int
}
```

Changes the brush of the active tool

* `change`: Can be: "increment-size", "decrement-size", "increment-angle", "decrement-angle", "flip-x", "flip-y", "flip-d", "rotate-90cw", "custom"
* `slot`: Custom brush slot (optional, only for "custom" change)

