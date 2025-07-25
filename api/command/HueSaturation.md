# HueSaturation

```lua
app.command.HueSaturation {
  ui=bool,
  channels=FilterChannels...,
  mode=string,
  hue=int,
  saturation=int,
  lightness=int,
  alpha=int
}
```

* `ui`: Shows the dialog on the screen, `true` by default. Set to `false` for automatic change brightness and/or contrast without asking the user for confirmation.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  By default it is equal to:
  [FilterChannels.RED](../filterchannels.md#filterchannelsred) |
  [FilterChannels.GREEN](../filterchannels.md#filterchannelsgreen) |
  [FilterChannels.BLUE](../filterchannels.md#filterchannelsblue) |
  [FilterChannels.GRAY](../filterchannels.md#filterchannelsgray).
* `mode`: `"hsl"` (default) or `"hsv"`
* `hue`: From `-180` to `180`
* `saturation`: From `-100` to `100`
* `lightness` (or `value`): From `-100` to `100`
* `alpha`: From `-100` to `100`
