# ChangeColor

```lua
app.command.ChangeColor {
    target=string
    change=string
}
```

Changes the current foreground or background color by moving up or down on the palette by index.

* `target`: Can be `"foreground"` or `"background"`
* `change`: Can be `"increment-index"` or `"decrement-index"`
