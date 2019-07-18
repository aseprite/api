# InvertColor

```lua
app.command.InvertColor {
  ui=true,
  channels=FilterChannels...
}
```

* `ui`: Shows the dialog on the screen, `true` by default. Set to
  `false` for automatic invert colors without asking to the user for
  the change.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  By default it is equal to:
  [FilterChannels.RED](../filterchannels.md#filterchannelsred) |
  [FilterChannels.GREEN](../filterchannels.md#filterchannelsgreen) |
  [FilterChannels.BLUE](../filterchannels.md#filterchannelsblue) |
  [FilterChannels.GRAY](../filterchannels.md#filterchannelsgray).
