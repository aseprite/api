# Aseprite API

This is the scripting API for Aseprite. Since Aseprite v1.2.10 you
will be able to create scripts with [Lua](https://www.lua.org/).

You can find [some examples](https://github.com/aseprite/Aseprite-Script-Examples)
for this API or some [tests](https://github.com/aseprite/aseprite/tree/main/tests/scripts).

## Where to start

Generally you will want to write a script to solve a problem or to do
a little experiment, so you have six options to approach your idea:

1. **Transform the active sprite**: In this case
   [app.sprite](api/app.md#appsprite) will give you access
   to the current sprite (it's `nil` if there is no active sprite,
   e.g. we are in the `Home` tab).
2. **Generate a new sprite** : Here the
   [Sprite()](api/sprite.md#sprite-1) function creates a new
   sprite and sets it as the active one. From there you can modify the
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
6. **Add new options to any menu**: In this case you'll need to create a
   [plugin with a script](api/plugin.md).

## API Changes

[API changes between versions](Changes.md#api-changes).

## Reference

Globals namespaces
  * [app](api/app.md#app)
  * [app.command](api/app_command.md#appcommand)
  * [app.fs](api/app_fs.md#appfs)
  * [app.os](api/app_os.md#appos)
  * [app.pixelColor](api/pixelcolor.md#apppixelcolor)
  * [app.theme](api/app_theme.md#apptheme)
  * [json](api/json.md#json)

Constants
  * [Align](api/align.md#align)
  * [AniDir](api/anidir.md#anidir)
  * [BlendMode](api/blendmode.md#blendmode)
  * [BrushPattern](api/brushpattern.md#brushpattern)
  * [BrushType](api/brushtype.md#brushtype)
  * [ColorMode](api/colormode.md#colormode)
  * [FilterChannels](api/filterchannels.md#filterchannel)
  * [Ink](api/ink.md#ink)
  * [MouseButton](api/mousebutton.md#mousebutton)
  * [MouseCursor](api/mousecursor.md#mousecursor)
  * [RangeType](api/rangetype.md#rangetype)
  * [SelectionMode](api/selectionmode.md#selectionmode)
  * [SpriteSheetDataFormat](api/spritesheetdataformat.md#spritesheetdataformat)
  * [SpriteSheetType](api/spritesheettype.md#spritesheettype)
  * [TilemapMode](api/tilemapmode.md#tilemapmode)
  * [TilesetMode](api/tilesetmode.md#tilesetmode)
  * [WebSocketMessageType](api/websocketmessagetype.md#websocketmessagetype)

Classes/objects
  * [Brush](api/brush.md#brush)
  * [Cel](api/cel.md#cel)
  * [Color](api/color.md#color)
  * [ColorSpace](api/colorspace.md#colorspace)
  * [Dialog](api/dialog.md#dialog)
  * [Editor](api/editor.md#editor)
  * [Events](api/events.md#events)
  * [Frame](api/frame.md#frame)
  * [GraphicsContext](api/graphicscontext.md#graphicscontext)
  * [Image](api/image.md#image)
  * [ImageSpec](api/imagespec.md#imagespec)
  * [KeyEvent](api/keyevent.md#keyevent)
  * [Layer](api/layer.md#layer)
  * [MouseEvent](api/mouseevent.md#mouseevent)
  * [Palette](api/palette.md#palette)
  * [Plugin](api/plugin.md#plugin)
  * [Point](api/point.md#point)
  * [Range](api/range.md#range)
  * [Rectangle](api/rectangle.md#rectangle)
  * [Selection](api/selection.md#selection)
  * [Site](api/site.md#site)
  * [Size](api/size.md#size)
  * [Slice](api/slice.md#slice)
  * [Sprite](api/sprite.md#sprite)
  * [Tag](api/tag.md#tag)
  * [Tile](api/tile.md#tile)
  * [Tileset](api/tileset.md#tileset)
  * [Timer](api/timer.md#timer)
  * [Tool](api/tool.md#tool)
  * [TouchEvent](api/touchevent.md#touchevent)
  * [Version](api/version.md#version)
  * [Uuid](api/uuid.md#uuid)
  * [WebSocket](api/websocket.md#websocket)
  * [Window](api/window.md#window)

Lua libraries
  * [Base library](api/base.md) and [Basic Functions in Lua manual](https://www.lua.org/manual/5.3/manual.html#6.1)
  * [Coroutine Manipulation](https://www.lua.org/manual/5.3/manual.html#6.2)
  * [String Manipulation](https://www.lua.org/manual/5.3/manual.html#6.4)
  * [UTF-8 Support](https://www.lua.org/manual/5.3/manual.html#6.5)
  * [Table Manipulation](https://www.lua.org/manual/5.3/manual.html#6.6)
  * [Mathematical Functions](https://www.lua.org/manual/5.3/manual.html#6.7)
  * [Operating System Facilities](https://www.lua.org/manual/5.3/manual.html#6.9)
    * Some functions like `os.remove`, `os.rename`, `os.exit`, `os.tmpname` are not available yet
    * Other functions like `os.execute` and `io.open` will ask for permissions to the user
  * [The Debug Library](https://www.lua.org/manual/5.3/manual.html#6.10)
