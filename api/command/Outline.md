# Outline

```lua
app.command.Outline {
  ui=true,
  channels=FilterChannels...,
  place='outside',
  matrix='circle',
  color=app.fgColor,
  bgColor=Color(),
  tiledMode='none'
}
```

* `ui`: Show the dialog on the screen, `true` by default.
* `channels`: A combination of [FilterChannels](../filterchannels.md#filterchannels) with
  [bitwise OR (`|`) operator](https://www.lua.org/manual/5.3/manual.html#3.4.2).
  The default value depends on the [active sprite](../app.md#appsprite) [color mode](../colormode.md):
  * [RGBA](../colormode.md#colormodergb):
    [FilterChannels.RGBA](../filterchannels.md#filterchannelsrgba)
  * [Grayscale](../colormode.md#colormodegray):
    [FilterChannels.GRAYA](../filterchannels.md#filterchannelsgraya)
  * [Indexed](../colormode.md#colormodeindexed):
    [FilterChannels.INDEX](../filterchannels.md#filterchannelsindex)
* `place`: `'inside'` or `'outside'`
* `matrix`: `'circle'`, `'square'`, `'horizontal'`, or `'vertical'`
* `color`: The [color](../color.md#color) of the outline
* `bgColor`: The [color](../color.md#color) of the background (the
  transparent color by default on transparent layers, or the first
  pixel at the top-left corner in background layer)
* `tiledMode`: `'none'`, `'x'`, `'y'`, `'both'`. By default it's
  `'none'` if there is no UI, or it's equal to `app.preferences.document(app.sprite).tiled.mode`
  when `ui` is `true`.
