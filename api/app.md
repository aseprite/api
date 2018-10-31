# app

The `app` global namespace.

## app.activeCel

Returns the active [Cel](cel.md) object.

## app.activeFrame

Returns the active frame number (1 is the first frame in the sprite).

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

## app.fgColor

Gets or sets the current foreground [color](color.md).

## app.bgColor

Gets or sets the current background [color](color.md). Remember that
some commands use the background color to clear the active layer.

## app.isUIAvailable

Returns true if the UI is available. E.g. if this is true you can use
[app.alert](#appalert) or [dialogs](dialog.md).

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

## app.command()

```lua
app.command.CommandName()
app.command.CommandName{param1:value1, param2:value2, ...}
```

Executes the give command named `CommandName` with the given
parameters.  You can look at the
[gui.xml](https://github.com/aseprite/aseprite/blob/master/data/gui.xml)
file to check a list of available commands.
