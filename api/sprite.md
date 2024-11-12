# Sprite

## Sprite()

```lua
local sprite = Sprite(width, height)
local sprite = Sprite(width, height, colorMode)
local sprite = Sprite(spec)
local sprite = Sprite(otherSprite)
local sprite = Sprite{ fromFile=string }
local sprite = Sprite{ fromFile=string, oneFrame=true }
```

Creates a new sprite with the given `width` and `height`. The
[color mode](colormode.md#colormode) is optional, [RGB](colormode.md#colormodergb)
by default.

The `spec` parameter is an [image specification](imagespec.md#imagespec) object.

If `otherSprite` is given (other `Sprite` object), the sprite is duplicated.

If `fromFile` is given, it indicates a file name (a string) and it's
like opening a new document with [`app.open()`](app.md#appopen).

When loading from a file, setting `oneFrame` to true will load with only the first animation frame.

## Sprite.width

```lua
local w = sprite.width
sprite.width = w
```

Returns or changes the sprite width. Use
[Sprite:resize](#spriteresize) if you want to change the sprite size
resizing layers, images, etc.

## Sprite.height

```lua
local h = sprite.height
sprite.height = h
```

Returns or changes the sprite height. Use
[Sprite:resize](#spriteresize) if you want to change the sprite size
resizing layers, images, etc.

## Sprite.bounds

```lua
local rectangle = sprite.bounds
```

Returns the bounds of the sprite as a
[rectangle](rectangle.md#rectangle) in the position `0,0`.
This is like calling `Rectangle{ x=0, y=0, width=sprite.width, height=sprite.height }`.

## Sprite.gridBounds

```lua
local rectangle = sprite.gridBounds
sprite.gridBounds = rectangle
```

Gets or sets the bounds of the sprite grid as a
[rectangle](rectangle.md#rectangle). By default this is 16x16 (with origin in 0,0)
but the default value can be [changed from *Edit > Preferences > Grid*](https://www.aseprite.org/docs/preferences/).

## Sprite.pixelRatio

```lua
local size = sprite.pixelRatio
sprite.pixelRatio = size
```

Gets or sets the pixel ratio of the sprite as a
[size](size.md#size).

## Sprite.selection

```lua
local selection = sprite.selection
sprite.selection = newSelection
```

Gets or sets the active sprite selection. This property is an instance
of the [Selection class](selection.md#selection) to manipulate the set of
selected pixels in the canvas.

## Sprite.filename

```lua
local name = sprite.filename
sprite.filename = newName
```

Gets or sets the name of the file from where this sprite was loaded or
saved. Or an empty string if this is a new sprite without an
associated file.

## Sprite.isModified

```lua
local modified = sprite.isModified
```

Returns true if the sprite is modified compared to the latest saved
state on disk.

## Sprite.colorMode

Returns the [color mode](colormode.md#colormode) of this sprite.

## Sprite.spec

```lua
local spec = sprite.spec
```

The [specification](imagespec.md#imagespec) for image in this sprite.

## Sprite.frames

```lua
for i,frame in ipairs(s.frames) do
  -- ...
end
for i = 1,#s.frames do
  -- s.frames[i]
end
```

An array of [frames](frame.md#frame).

## Sprite.palettes

An array of [palettes](palette.md#palette). Generally it contains only one
palette (`sprite.palettes[1]`).

In the future we'll support multiple palettes to create
[color cycling animations](https://en.wikipedia.org/wiki/Color_cycling).

## Sprite.layers

```lua
for i,layer in ipairs(s.layers) do
  -- ...
end
for i = 1,#s.layers do
  -- s.layers[i]
end
```

An array of [layers](layer.md#layer).

## Sprite.cels

```lua
for i,cel in ipairs(s.cels) do
  -- ...
end
for i = 1,#s.cels do
  -- s.cels[i]
end
```

An array of [cels](cel.md#cel).

## Sprite.tags

```lua
for i,tag in ipairs(s.tags) do
  -- ...
end
for i = 1,#s.tags do
  -- s.tags[i]
end
```

An array of [tags](tag.md#tag).

## Sprite.slices

```lua
for i,slice in ipairs(s.slices) do
  -- ...
end
for i = 1,#s.slices do
  -- s.slices[i]
end
```

An array of [slices](slice.md#slice).

## Sprite.backgroundLayer

Returns the [background
layer](https://www.aseprite.org/docs/layers/#background-layer) a
[layer](layer.md#layer) object or `nil` if the sprite doesn't contain a
background layer.

## Sprite.transparentColor

```lua
local number = sprite.transparentColor
sprite.transparentColor = number
```

The transparent color is an intenger that specifies what index (`0` by
default) is the transparent color in transparent layers on indexed
sprites.

## Sprite.color

```lua
local color = sprite.color
sprite.color = color
```

Gets or sets the user-defined [color](color.md#color) of this sprite.
This color is used to display the tab in the main window of this
sprite.

## Sprite.data

```lua
local data = sprite.data
sprite.data = data
```

Gets or sets the user-defined data related to this sprite (a text string).

## Sprite.properties

Access user-defined and extension-defined
[properties](properties.md#properties) of this sprite.

## Sprite:resize()

```lua
sprite:resize(width, height)
sprite:resize(size)
```

Resize the sprite (and all frames/cels) to the given dimensions. See
[Size class](size.md#size).

## Sprite:crop()

```lua
sprite:crop(x, y, width, height)
sprite:crop(rectangle)
```

Crops the sprite to the given dimensions. See the
[Rectangle class](rectangle.md#rectangle).

## Sprite:saveAs()

```lua
sprite:saveAs(filename)
```

Saves the sprite to the given file and marks the sprite as saved so
closing it won't ask to save changes.

## Sprite:saveCopyAs()

```lua
sprite:saveCopyAs(filename)
```

Saves a copy of the sprite in the given file but doesn't change the
saved state of the sprite, if the sprite is modified and then try to
close it, the user will be asked to save changes.

## Sprite:close()

```lua
sprite:close()
```

Closes the sprite. This doesn't ask the user to save changes. If you
want to do the classic *File > Close* where the user is asking to save
changes, you can use `app.command.CloseFile()`.

## Sprite:loadPalette()

```lua
sprite:loadPalette(filename)
```

Sets the sprite palette loading it from the given file.

The same can be achieved using [`Palette{ fromFile }`](palette.md#palette):

```lua
sprite:setPalette(Palette{ fromFile=filename })
```

## Sprite:setPalette()

```lua
sprite:setPalette(palette)
```

Changes the sprite [palette](palette.md#palette).

## Sprite:assignColorSpace

```lua
local colorSpace = ColorSpace{ sRGB=true }
sprite:assignColorSpace(colorSpace)
```

Assign a new [color space](colorspace.md#colorspace) to the sprite without
modifying the sprite pixels.

## Sprite:convertColorSpace

```lua
local colorSpace = ColorSpace{ sRGB=true }
sprite:convertColorSpace(colorSpace)
```

Converts all the sprite pixels to a new [color space](colorspace.md#colorspace)
so the image looks the same as in the previous color space (all pixels
will be adjusted to the new color space).

## Sprite:newLayer()

```lua
local layer = sprite:newLayer()
```

Creates a new [layer](layer.md#layer) at the top of the layers stack.

## Sprite:newGroup()

```lua
local layerGroup = sprite:newGroup()
```

Creates a new empty [layer group](layer.md#layer) at the top of the layers stack.

## Sprite:deleteLayer()

```lua
sprite:deleteLayer(layer)
sprite:deleteLayer(layerName)
```

Deletes the given [layer](layer.md#layer) or the layer with the given `layerName` (a string).

## Sprite:newFrame()

```lua
local frame = sprite:newFrame(frame)
local frame = sprite:newFrame(frameNumber)
```

Creates a copy of the given [frame](frame.md#frame) object or frame number
and returns a [`Frame`](frame.md#frame) that points to the newly created
frame in `frameNumber` position.

## Sprite:newEmptyFrame()

Creates a new empty frame in the given `frameNumber` (an integer) and
returns the new [frame](frame.md#frame).

## Sprite:deleteFrame()

```lua
sprite:deleteFrame(frame)
```

## Sprite:newCel()

```lua
cel = sprite:newCel(layer, frame)
cel = sprite:newCel(layer, frame, image, position)
```

Creates a new [cel](cel.md#cel) in the given [layer](layer.md#layer) and `frame`
number. If the [image](image.md#image) is not specified, a new image will be
created with the size of the sprite canvas. The [position](point.md#point)
is a point to locate the image.

## Sprite:deleteCel()

```lua
sprite:deleteCel(cel)
sprite:deleteCel(layer, frame)
```

Deletes the given [cel](cel.md#cel). If the cel is from a transparent
layer, the cel is completely deleted, but if the cel is from a
background layer, the cel will be delete with the
[background color](app.md#appbgcolor).

## Sprite:newTag()

```lua
local tag = sprite:newTag(fromFrameNumber, toFrameNumber)
```

Creates a new [tag](tag.md#tag) in the given frame range and with the given name.

## Sprite:deleteTag()

```lua
sprite:deleteTag(tag)
sprite:deleteTag(tagName)
```

Deletes the given [tag](tag.md#tag).

## Sprite:newSlice()

```lua
local slice = sprite:newSlice()
local slice = sprite:newSlice(Rectangle)
```

Returns a new [slice](slice.md#slice).

## Sprite:deleteSlice()

```lua
sprite:deleteSlice(slice)
sprite:deleteSlice(sliceName)
```

Deletes the given [slice](slice.md#slice).

## Sprite:newTileset()

```lua
local tileset = sprite:newTileset()
local tileset = sprite:newTileset(Grid)
local tileset = sprite:newTileset(Rectangle)
local tileset = sprite:newTileset(Grid, numTiles)
local tileset = sprite:newTileset(Rectangle, numTiles)
local tileset = sprite:newTileset(anotherTileset)
```

Returns a new [tileset](tileset.md#tileset) and adds it to the
sprite's tilesets.

If no parameters are given, the resulting tileset will have just one
empty tile and a tile size equal to the active [sprite grid size](#spritegridbounds).

If Grid or Rectangle is specified it is used to set the resulting
tileset's origin and tile size.

numTiles specifies the number of tiles we want the tileset to contain
initially.

If another tileset is passed as the only parameter, the result is a
duplicate of it. Take into consideration that the passed tileset
cannot belong to another sprite.

## Sprite:deleteTileset()

```lua
sprite:deleteTileset(tileset)
sprite:deleteTileset(tilesetIndex)
```

Deletes the given [tileset](tileset.md#tileset) from the sprite's tilesets.

## Sprite:newTile()

```lua
local tile = sprite:newTile(tileset [, tileIndex])
```

Inserts an empty [tile](tile.md#tile) into the given
[tileset](https://github.com/aseprite/api/blob/next-version/api/tileset.md#tileset)
at a given `tileIndex`. If `tileIndex` is not provided, the new tile
is added to the end of the tileset. This method generates undo
information, so you could use it as an individual operation or in a
[transaction](https://github.com/aseprite/api/blob/main/api/app.md#apptransaction).

## Sprite:deleteTile()

```lua
local tile = tileset:tile(tileIndex)
Sprite:deleteTile(tile)
Sprite:deleteTile(tileset, tileIndex)
```

Removes a `tile` from a
[tileset](https://github.com/aseprite/api/blob/next-version/api/tileset.md#tileset). This
method generates undo information, so you could use it as an
individual operation or in a
[transaction](https://github.com/aseprite/api/blob/main/api/app.md#apptransaction).

## Sprite:flatten()

```lua
sprite:flatten()
```

Flatten all layers of the sprite into one layer.
It's like calling `app.commands.FlattenLayers()`.

## Sprite.events

Returns the [`Events`](events.md#events) object to associate functions
that can act like listeners of specific `Sprite` events. E.g.

```lua
sprite.events:on('change',
  function(ev)
    print('The sprite has changed')
  end)
```

A special `ev` argument can be sent to the listener. Which generally
is a table, but it can be `nil` for older version of Aseprite or
events that don't support it.

Available events for a `Sprite`:

* `'change'`: When sprite content changed because we perform some
  action on it (also called when we undo/redo those actions). Since
  Aseprite v1.2.41, you can access `ev.fromUndo` property which is
  `true` if the change came from a undo/redo/undo history event (and
  not from a direct user change in the sprite).
* `'filenamechange'`: When the filename associated to a sprite
  changes.

## Sprite.tileManagementPlugin

```lua
local id = sprite.tileManagementPlugin
sprite.tileManagementPlugin = newId
```

Special property to disable Aseprite
[tile management UI](https://aseprite.org/docs/tilemap) and use
an external plugin to handle tilesets and tilemaps in this sprite.

This property is used by the
[Attachment-System](https://github.com/aseprite/Attachment-System)
plugin, but any extension can create a totally customized way to
handle tiles (and disable the standard UI to avoid conflicts).

**Warning**: If a sprite has this property set, another plugin
shouldn't change it, because it might break the tilesets/tilemaps
structure.
