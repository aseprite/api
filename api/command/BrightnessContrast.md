# BrightnessContrast

```lua
app.command.BrightnessContrast {
  ui=true,
  channels=FilterChannels...,
  brightness=0,
  contrast=0
}
```

* `ui`: Shows the dialog on the screen, `true` by default. Set to
  `false` for automatic change brightness and/or contrast without
  asking to the user for the change.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  By default it is equal to:
  [FilterChannels.RED](../filterchannels.md#filterchannelsred) |
  [FilterChannels.GREEN](../filterchannels.md#filterchannelsgreen) |
  [FilterChannels.BLUE](../filterchannels.md#filterchannelsblue) |
  [FilterChannels.GRAY](../filterchannels.md#filterchannelsgray).
* `brightness`: Brightness factor (`0` by default), a value between `-100` and `100`.
* `contrast`: Contrast factor (`0` by default), a value between `-100` and `100`.
