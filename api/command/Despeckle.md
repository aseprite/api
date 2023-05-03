# Despeckle

```lua
app.command.Despeckle {
  ui=true,
  channels=...,
  width=3,
  height=3,
  tiledMode=none,
}
```

* `ui`: Show the dialog on the screen, `true` by default.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  By default it is equal to:
  [FilterChannels.RED](../filterchannels.md#filterchannelsred) |
  [FilterChannels.GREEN](../filterchannels.md#filterchannelsgreen) |
  [FilterChannels.BLUE](../filterchannels.md#filterchannelsblue) |
  [FilterChannels.GRAY](../filterchannels.md#filterchannelsgray).
* `width`: Width of the convolution matrix to calculate the median. `3` by default.
* `height`: Height of the convolution matrix to calculate the median. `3` by default.
* `tiledMode`: `'none'`, `'x'`, `'y'`, `'both'`. By default it's
  `'none'` if there is no UI, or it's equal to `app.preferences.document(app.sprite).tiled.mode`
  when `ui` is `true`.
