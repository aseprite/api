# ConvolutionMatrix

```lua
app.command.ConvolutionMatrix {
  ui=true,
  channels=FilterChannels...,
  tiledMode=none,
  fromResource=string
}
```

* `ui`: Shows the dialog on the screen, `true` by default. Set to
  `false` to apply the convolution matrix filter automatically without
  asking to the user for the change.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  By default it is equal to:
  [FilterChannels.RED](../filterchannels.md#filterchannelsred) |
  [FilterChannels.GREEN](../filterchannels.md#filterchannelsgreen) |
  [FilterChannels.BLUE](../filterchannels.md#filterchannelsblue) |
  [FilterChannels.GRAY](../filterchannels.md#filterchannelsgray).
* `tiledMode`: `'none'`, `'x'`, `'y'`, `'both'`. By default it's
  `'none'` if there is no UI, or it's equal to `app.preferences.document(app.sprite).tiled.mode`
  when `ui` is `true`.
* `fromResource`: Name of [pre-defined convolution matrix](https://github.com/aseprite/aseprite/blob/a70a3a11c71ae96eb6af3756525182e88129ffcd/data/convmatr.def#L34).

*Note*: In future versions this function should support creating
customized convolution matrices.
