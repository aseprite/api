# app

The `app` global namespace.

## app.site

Active [site](site.md#site) (active image, layer, frame, sprite, etc.).

## app.range

[Range](range.md#range) member represents the active selection from an objects collection. It returns a sorted list of selected frames, or cels, or layers, or colors, etc.

## app.activeCel

Gets or sets the active [Cel](cel.md#cel) object.

## app.activeFrame

Gets or sets the active frame number (1 is the first frame in the sprite).

**WARNING**: This function has a bug in Aseprite v1.2.10-beta2,
returns `nil` if we are in the first frame of the sprite. Also it
returns a number, but in the future it will returns a
[frame](frame.md#frame) object, you can use an auxiliary function at the
moment:

```lua
local function activeFrameNumber()
  local f = app.activeFrame
  if f == nil then
    return 1
  else
    return f
  end
end
```

## app.activeImage

```lua
local image = app.activeImage
```

Returns the active image, an [Image](image.md#image) object.

## app.activeLayer

Returns the active layer, a [Layer](layer.md#layer) object.

## app.activeSprite

```lua
local sprite = app.activeSprite
```

Returns the active sprite, a [Sprite](sprite.md#sprite) object.

## app.activeTag

Returns the active [tag](tag.md#tag), which is the tag located at the
[active frame](#appactiveframe).

## app.activeTool

Returns the active tool (a [Tool](tool.md#tool) object) selected in
the [tool bar](https://www.aseprite.org/docs/workspace/).

## app.activeBrush

Returns the active brush (a [Brush](brush.md#brush) object) selected
in the [context bar](https://www.aseprite.org/docs/workspace/).

## app.pixelColor

This [pixelColor namespace](pixelcolor.md#apppixelcolor) contains internal functions
to handle color at the lowest level.

## app.version

Returns the Aseprite version number as a [`Version`](version.md#version) object (e.g. `Version("1.2.10-beta1")`).

## app.apiVersion

Returns the API version. See the [changes file](../Changes.md#api-changes) between
version to know what offer each API version.

## app.fgColor

Gets or sets the current foreground [color](color.md#color).

## app.bgColor

Gets or sets the current background [color](color.md#color). Remember that
some commands use the background color to clear the active layer.

## app.isUIAvailable

Returns true if the UI is available. E.g. if this is true you can use
[app.alert](#appalert) or [dialogs](dialog.md#dialog).

## app.sprites

```lua
for i,sprite in ipairs(app.sprites) do
  -- do something with each sprite...
end
```

Returns an array of [sprites](sprite.md#sprite).

## app.params

This is a table with parameters specified as
[`--script-param key=value`](https://www.aseprite.org/docs/cli/#script-param) in the
[CLI](https://www.aseprite.org/docs/cli/) or as `<param>` in
`user.aseprite-keys` or
[`gui.xml`](https://github.com/aseprite/aseprite/blob/master/data/gui.xml)
file.

## app.alert()

```lua
app.alert "Text"
app.alert("Text")
app.alert{title="Title", text="Text", buttons="OK"}
app.alert{title="Title", text="Text", buttons={"OK", "Cancel"}}
app.alert{title="Title", text={"Line 1", "Line 2", ...}, buttons={"Yes", "No", "Cancel", ...}}
```

Shows an alert message. If `buttons` are not specified, it will show a
message box with the `OK` button only.

Returns an integer with the selected button i.e. 1 if the first button
was clicked, 2 if the second one, etc. Example:

```lua
local result = app.alert{ title="Warning",
                          text="Save Changes?",
                          buttons={"Yes", "No"}}
if result == 1 then
  app.alert "Yes was pressed"
end
```

## app.open()

```lua
app.open(filename)
```

Opens a new sprite loading it from the given filename. Returns an
instance of the [Sprite class](sprite.md#sprite) or `nil` if something went
wrong.

## app.exit()

```lua
app.exit()
```

Closes the application. It's like clicking *File > Exit* menu option.

## app.transaction()

```lua
app.transaction(
  function()
    ...
  end)
```

Creates a new transaction so you can group several sprite
modifications in just one undo/redo operation.

The function in the argument is called inside the transaction, if the
function fails, the whole transaction is undone. If the function
successes, the transaction is committed and then all actions will be
grouped in just one undo/redo operation.

## app.command

Check the [app.command](app_command.md#appcommand) documentation.

## app.preferences

Check the [app.preferences](app_preferences.md#apppreferences) documentation.

## app.fs

Check the [app.fs](app_fs.md#appfs) documentation.

## app.refresh()

```lua
app.refresh()
```

This function is available just in case you see that your script
updates the sprite but the screen is not showing the updated state of
the sprite. It should not be needed, but it's here just in case that
something is not working right on the Aseprite side.

## app.undo()

```lua
app.undo()
```

Undoes the latest operation in the [`activeSprite`](#appactivesprite).
It's like calling `app.command.Undo()` (the *Edit > Undo*  menu option).

## app.redo()

```lua
app.redo()
```

Redoes the latest undone operation in the
[`activeSprite`](#appactivesprite).  It's like calling
`app.command.Redo()` (the *Edit > Redo*  menu option).

## app.useTool()

```lua
app.useTool{
 tool=string,
 color=Color,
 brush=Brush,
 points={ Point, Point, .... },
 cel=Cel,
 layer=Layer,
 frame=Frame
}
```

Simulates an user stroke in the canvas using the given tool.

* `tool`: A string with a well known tool ID (`rectangular_marquee`,
  `elliptical_marquee`, `lasso`, `polygonal_lasso`, `magic_wand`,
  `pencil`, `spray`, `eraser`, `eyedropper`, `zoom`, `hand`, `move`,
  `slice`, `paint_bucket`, `gradient`, `line`, `curve`, `rectangle`,
  `filled_rectangle`, `ellipse`, `filled_ellipse`, `contour`,
  `polygon`, `blur`, `jumble`) or a [tool](tool.md#tool) object
* `color`: A [color](color.md#color) object to draw with the given tool
* `brush`: A [brush](brush.md#brush) object to draw the points
* `points`: An array of [points](point.md#point) in the sprite canvas which
  simulate the position of where the user put the mouse to draw with
  the given tool.
* And we can specify the `cel` or `layer`/`frame` where to draw:
  * `cel`: The specific [cel](cel.md#cel) where we want to use the tool/draw with the tool (by default [app.activeCel](app.md#appactivecel))
  * `layer`: The [layer](layer.md#layer) where we want to use the tool/draw with the tool (by default [app.activeLayer](app.md#appactivelayer))
  * `frame`: The [frame](frame.md#frame) where to draw (by default [app.activeFrame](app.md#appactiveframe))
