# AddColor

```lua
app.command.AddColor {
  source=string,
  color=Color
}
```

Adds a new color into the palette.

* `source`: Can be `"fg"`, `"bg"`, or `"color"` (default). To add the foreground, background, or a specific color respectively.
* `color`: A [Color](../color.md#color) instance to add too the palette.

## Example

```lua
app.command.AddColor {
  color=Color(255, 0, 0)
}

app.command.AddColor {
  source="fg"
}
```
