# Aseprite API

This is the scripting API for Aseprite. Since Aseprite v1.2.10 you
will be able to create scripts with [Lua](https://www.lua.org/).

You can find some tests/examples for this API
[here](https://github.com/aseprite/tests/tree/master/scripts).

## Where to start

Generally you will want to write a script to solve a problem or to do
a little experiment, so you have five main options to approach your idea:

1. **Transform the active sprite**: In this case
   [app.activeSprite](api/app.md#appactivesprite) will give you access
   to the current sprite (it's `nil` if there is no active sprite,
   e.g. we are in the `Home` tab).
2. **Generate a new sprite** : Here the
   [Sprite()](api/sprite.md#sprite-1) function creates a new
   sprite and sets is as the active one. From there you can modify the
   [Sprite](api/sprite.md#sprite) object as you want.
3. **Open one or several existent files**: You can use
   [app.open](api/app.md#appopen) to load a sprite from the disk and
   then modify it.
4. **Save the modified sprite**: After you have done some modifications
   to a sprite, you might want to save the result directly to the
   disk, [Sprite:saveCopyAs()](api/sprite.md#spritesavecopyas) function is a
   good option to export the modified sprite.
5. **Show a dialog to the user**: The [Dialog](api/dialog.md#dialog) object
   gives you the possibility to show controls to the user to enter values.

## API Changes

[API changes between versions](Changes.md).

## Reference

* Globals namespaces
  * [app](api/app.md#app)
  * [app.pixelColor](api/pixelcolor.md#pixelcolor)
* Constants
  * [AniDir](api/anidir.md#anidir)
  * [BlendMode](api/blendmode.md#blendmode)
  * [ColorMode](api/colormode.md#colormode)
  * [RangeType](api/rangetype.md#rangetype)
* Classes/objects
  * [Cel](api/cel.md#cel)
  * [Color](api/color.md#color)
  * [Dialog](api/dialog.md#dialog)
  * [Frame](api/frame.md#frame)
  * [Image](api/image.md#image)
  * [ImageSpec](api/imagespec.md#imagespec)
  * [Layer](api/layer.md#layer)
  * [Palette](api/palette.md#palette)
  * [Point](api/point.md#point)
  * [Range](api/range.md#range)
  * [Rectangle](api/rectangle.md#rectangle)
  * [Selection](api/selection.md#selectin)
  * [Size](api/size.md#size)
  * [Slice](api/slice.md#slice)
  * [Sprite](api/sprite.md#sprite)
  * [Tag](api/tag.md#tag)
* Lua libraries
  * [Basic Functions](https://www.lua.org/manual/5.3/manual.html#6.1)
  * [Coroutine Manipulation](https://www.lua.org/manual/5.3/manual.html#6.2)
  * [String Manipulation](https://www.lua.org/manual/5.3/manual.html#6.4)
  * [UTF-8 Support](https://www.lua.org/manual/5.3/manual.html#6.5)
  * [Table Manipulation](https://www.lua.org/manual/5.3/manual.html#6.6)
  * [Mathematical Functions](https://www.lua.org/manual/5.3/manual.html#6.7)
  * [Operating System Facilities](https://www.lua.org/manual/5.3/manual.html#6.9)
    * Some functions like `os.remove`, `os.rename`, `os.exit`, `os.tmpname` are not available yet
    * Other functions like `os.execute` and `io.open` will ask for permissions to the user
  * [The Debug Library](https://www.lua.org/manual/5.3/manual.html#6.10)
