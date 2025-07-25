# Rotate

```lua
app.command.Rotate {
  ui=bool,
  target=string,
  angle=string,
}
```

Rotates the sprite or mask, depending on `target`.

**Note**: Mask rotation only works in UI mode (regardless of the `ui` parameter).

* `ui`: Shows the rotation progress dialog, `true` by default. Set to `false` to rotate automatically.
* `target`: Can be `"default"` or `"mask"`.
* `angle`: The angle of rotation.
