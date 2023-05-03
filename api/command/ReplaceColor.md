# ReplaceColor

```lua
app.command.ReplaceColor {
  ui=true,
  channels=FilterChannels...,
  from=Color,
  to=Color,
  tolerance=0
}
```

* `ui`: Show the dialog on the screen, `true` by default. Set to
  `false` for automatic replacement without asking to the user for the
  change. When the dialog is displayed to the user,
  `app.command.ReplaceColor()` will return a `true` or `false` value
  indicating if the replacement was accepeted or cancelled
  respectively.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  The default value depends on the [active sprite](../app.md#appsprite) [color mode](../colormode.md):
  * [RGBA](../colormode.md#colormodergb):
    [FilterChannels.RGBA](../filterchannels.md#filterchannelsrgba)
  * [Grayscale](../colormode.md#colormodegray):
    [FilterChannels.GRAYA](../filterchannels.md#filterchannelsgraya)
  * [Indexed](../colormode.md#colormodeindexed):
    [FilterChannels.INDEX](../filterchannels.md#filterchannelsindex)
* `from`: [Color](../color.md#color) to replace (it's the [foreground color](../app.md#appfgcolor) by default)
* `to`: [Color](../color.md#color) to replace (it's the [background color](../app.md#appbgcolor) by default)
* `tolerance`: Maximum allowed difference between `from` and the pixel
  in the image to apply the replacement.
