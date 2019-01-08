# app

The `app` global namespace.

## app.site

Active [site](site.md#site) (active image, layer, frame, sprite, etc.).

## app.range

Active [range](range.md#range) in the timeline.

## app.activeCel

Gets or sets the active [Cel](cel.md) object.

## app.activeFrame

Gets or sets the active frame number (1 is the first frame in the sprite).

**WARNING**: This function has a bug in Aseprite v1.2.10-beta2,
returns `nil` if we are in the first frame of the sprite. Also it
returns a number, but in the future it will returns a
[frame](frame.md) object, you can use an auxiliary function at the
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

Returns the active image, an [Image](image.md) object.

## app.activeLayer

Returns the active layer, a [Layer](layer.md) object.

## app.activeSprite

```lua
local sprite = app.activeSprite
```

Returns the active sprite, a [Sprite](sprite.md) object.

## app.activeTag

Returns the active [tag](tag.md), which is the tag located at the
[active frame](#appactiveframe).

## app.pixelColor

This [pixelColor namespace](pixelcolor.md) contains internal functions
to handle color at the lowest level.

## app.version

Returns the Aseprite version number as a string (e.g. `"1.2.10-beta1"`).

## app.apiVersion

Returns the API version. See the [changes file](../Changes.md) between
version to know what offer each API version.

## app.fgColor

Gets or sets the current foreground [color](color.md).

## app.bgColor

Gets or sets the current background [color](color.md). Remember that
some commands use the background color to clear the active layer.

## app.isUIAvailable

Returns true if the UI is available. E.g. if this is true you can use
[app.alert](#appalert) or [dialogs](dialog.md).

## app.sprites

```lua
for i,sprite in ipairs(app.sprites)
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

## app.open()

```lua
app.open(filename)
```

Opens a new sprite loading it from the given filename. Returns an
instance of the [Sprite class](sprite.md) or `nil` if something went
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
