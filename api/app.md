# app

The `app` global namespace.

## app.activeImage

```lua
local image = app.activeImage
```

Returns the active image, an [Image](image.md) object.

## app.activeSprite

```lua
local sprite = app.activeSprite
```

Returns the active sprite, a [Sprite](sprite.md) object.

## app.pixelColor

This [pixelColor namespace](pixelcolor.md) contains internal functions
to handle color at the lowest level.

## app.version

Returns the Aseprite version number as a string (e.g. `"1.2.10-beta1"`).

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
