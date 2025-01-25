# app

The `app` global namespace.

## app.site

Active [site](site.md#site) (active image, layer, frame, sprite, etc.).

## app.range

[Range](range.md#range) member represents the active selection from an objects collection. It returns a sorted list of selected frames, or cels, or layers, or colors, etc.

## app.cel

Gets or sets the active [Cel](cel.md#cel) object.

## app.frame

```lua
local frame = app.frame
assert(frame.sprite == app.sprite)
app.frame = app.sprite.frames[2] -- go to the second frame

app.frame = 3 -- you can assign a frame number directly
app.frame = 1 -- 1 is the first frame of the sprite
```

Returns a [Frame object](frame.md#frame) that represents the active
frame in the focused sprite editor. You can set this property
assigning a frame number directly to jump to another frame.

To known the active frame number use [`app.frame.frameNumber`](frame.md#frameframenumber)

## app.image

```lua
local image = app.image
```

Returns the active image, an [Image](image.md#image) object.

## app.layer

Returns the active layer, a [Layer](layer.md#layer) object.

## app.sprite

```lua
local sprite = app.sprite
```

Returns the active sprite, a [Sprite](sprite.md#sprite) object.

## app.tag

Returns the active [tag](tag.md#tag), which is the tag located at the
[active frame](#appframe).

## app.tool

Returns the active tool (a [Tool](tool.md#tool) object) selected in
the [tool bar](https://www.aseprite.org/docs/workspace/).

## app.brush

Returns the active brush (a [Brush](brush.md#brush) object) selected
in the [context bar](https://www.aseprite.org/docs/workspace/).

## app.editor

Returns the active editor (a [Editor](editor.md#editor) object).

## app.window

Returns the main window (a [Window](window.md#window) object).

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
[app.alert](#appalert) or [dialogs](dialog.md#dialog). The UI is not available
when we run in [--batch mode](https://www.aseprite.org/docs/cli/#batch).

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
[`gui.xml`](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
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

app.transaction(
  string,
  function()
    ...
  end)
```

Creates a new transaction so you can group several sprite
modifications in just one undo/redo operation. If a string is given as
first argument, that string will be used as the label of this
undo/redo action (which can be seen in the *Edit > Undo History*
window).

The given function is called inside the transaction, if the function
fails, the whole transaction is undone (i.e. all the steps executed so
far will be reversed). If the function successes, the transaction is
committed and then all actions will be grouped in just one undo/redo
operation.

You can cancel/reverse/cause an explicit failure of the transaction
calling the `error()` Lua function, e.g:

```lua
app.transaction(
  function()
    ...
    if something_is_wrong then
      error() -- this stops the function and doesn't continue with the
              -- following lines / the actions so far will be reversed
              -- automatically leaving the sprite intact
    end
    ...
  end)
```

## app.command

Check the [app.command](app_command.md#appcommand) documentation.

## app.preferences

Check the [app.preferences](app_preferences.md#apppreferences) documentation.

## app.fs

Check the [app.fs](app_fs.md#appfs) documentation.

## app.theme

Check the [app.theme](app_theme.md#apptheme) documentation.

## app.os

Check the [app.os](app_os.md#appos) documentation.

## app.uiScale

```
local scale = app.uiScale
```

Returns the [UI Elements Scaling](https://www.aseprite.org/docs/preferences/)
value specified in *Edit > Preferences* as an scale factor (1 for 100%, 2 for 200%, etc.)

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

Undoes the latest operation in the [`active sprite`](#appsprite).
It's like calling `app.command.Undo()` (the *Edit > Undo*  menu option).

## app.redo()

```lua
app.redo()
```

Redoes the latest undone operation in the
[`active sprite`](#appsprite).  It's like calling
`app.command.Redo()` (the *Edit > Redo*  menu option).

## app.useTool()

```lua
app.useTool{
 tool=string,
 color=Color,
 bgColor=Color,
 brush=Brush,
 points={ Point, Point, .... },
 cel=Cel,
 layer=Layer,
 frame=Frame,
 ink=Ink,
 button=MouseButton.LEFT | MouseButton.RIGHT,
 opacity=integer,
 contiguous=false | true,
 tolerance=integer,
 freehandAlgorithm=0 | 1,
 selection=SelectionMode.REPLACE | SelectionMode.ADD | SelectionMode.SUBTRACT | SelectionMode.INTERSECT,
 tilemapMode=TilemapMode.PIXELS | TilemapMode.TILES,
 tilesetMode=TilesetMode.MANUAL | TilesetMode.AUTO | TilesetMode.STACK,
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
* `selection`: What to do with the selection, only for selection-like
  tools (`rectangular_marquee`, `magic_wand`, etc.). The default value
  when the [UI is enabled](#appisuiavailable) will be
  `app.preferences.selection.mode`, in CLI mode it's
  `SelectionMode.REPLACE`.
* And we can specify the `cel` or `layer`/`frame` where to draw:
  * `cel`: The specific [cel](cel.md#cel) where we want to use the tool/draw with the tool (by default [app.cel](app.md#appcel))
  * `layer`: The [layer](layer.md#layer) where we want to use the tool/draw with the tool (by default [app.layer](app.md#applayer))
  * `frame`: The [frame](frame.md#frame) where to draw (by default [app.frame](app.md#appframe))

## app.events

Returns the [`Events`](events.md#events) object to associate functions
that can act like listeners of specific `app` events. E.g.

```lua
app.events:on('sitechange',
  function()
    print('Now we are located in other sprite, layer, or frame')
  end)
```

Available events for `app`:

* `'sitechange'`: When the user selects other sprite, layer, or frame.
* `'fgcolorchange'`: When the [Foreground color](https://www.aseprite.org/docs/color-bar/#foreground-color) in the color bar is changed.
* `'bgcolorchange'`: When the [Background color](https://www.aseprite.org/docs/color-bar/#background-color) in the color bar is changed.
* `'beforecommand'`: Before executing any command in the program.
* `'aftercommand'`: After executing any command in the program.

The `'beforecommand'` and `'aftercommand'` events receive an `ev`
argument with the name of the command (`ev.name`) and the params
(`ev.params`). `'beforecommand'` includes a `ev.stopPropagation()`
function to cancel the event, e.g. in case that you've handled the
event in a custom way.

E.g. This code catches the *Edit > Cut* command and convert it to a *Copy*:
```lua
app.events:on('beforecommand',
  function(ev)
    if ev.name == "Cut" then
      app.command.Copy()   -- call Copy command
      ev.stopPropagation() -- and cancel the Cut
    end
  end)
```

# Deprecated Names

The following fields were replaced with new alternatives (generally
shorter) names. These will not be removed from the API, so we can
offer backward compatibility with old scripts.

## app.activeSprite

Deprecated. Use [app.sprite](#appsprite).

## app.activeLayer

Deprecated. Use [app.layer](#applayer).

## app.activeFrame

Deprecated. Use [app.frame](#appframe).

**WARNING**: This function had two bugs
in [Aseprite v1.2.10-beta2](https://www.aseprite.org/release-notes/12/#aseprite-v1-2-10-beta2)
where 1) it returned `nil` if we were in the first frame of the
sprite, and 2) it returned a number. Since Aseprite v1.2.10-beta3 it
started to return a [Frame](frame.md#frame) object.

## app.activeCel

Deprecated. Use [app.cel](#appcel).

## app.activeImage

Deprecated. Use [app.image](#appimage).

## app.activeTag

Deprecated. Use [app.tag](#apptag).

## app.activeTool

Deprecated. Use [app.tool](#apptool).

## app.activeBrush

Deprecated. Use [app.brush](#appbrush).
