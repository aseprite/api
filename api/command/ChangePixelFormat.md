# ChangePixelFormat

```lua
app.command.ChangePixelFormat {
  format=string
}
```

Changes the [ColorMode](../colormode.md) of the active [sprite](../sprite.md)

* `format`: Can be `"rgb"`, `"gray"` or `"indexed"`.

## Example

```lua
app.command.ChangePixelFormat {
  format="indexed"
}
```

