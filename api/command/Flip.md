# Flip

```lua
app.command.Flip {
  target=string
  orientation=string
}
```

Flips the whole sprite or the current selection mask, either vertically or horizontally.

Note: When specifying `target=mask` without a UI or with no active mask, the entire sprite will be flipped.

* `target`: Can be `"mask"` or `"sprite"`. Defaults to `"sprite"`.
* `change`: Can be `"vertical"` or `"horizontal"`. Defaults to `"horizontal"`.
