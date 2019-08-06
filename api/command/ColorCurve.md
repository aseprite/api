# ColorCurve

```lua
app.command.ColorCurve {
  ui=true,
  channels=FilterChannels...,
  curve={ Point, Point, Point... }
}
```

* `ui`: Shows the dialog on the screen, `true` by default. Set to
  `false` to apply the color curve filter automatically without asking
  to the user for the change.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  By default it is equal to:
  [FilterChannels.RED](../filterchannels.md#filterchannelsred) |
  [FilterChannels.GREEN](../filterchannels.md#filterchannelsgreen) |
  [FilterChannels.BLUE](../filterchannels.md#filterchannelsblue) |
  [FilterChannels.GRAY](../filterchannels.md#filterchannelsgray).
* `curve`: Array of [points](../point.md#point) where X is the input
  value and Y the output value.

## Example

```lua
app.command.ColorCurve {
  ui=true,
  channels=FilterChannels.RED,
  curve={ { 0, 0 }, { 255, 128 } }
}
```
