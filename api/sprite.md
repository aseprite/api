# Sprite

## Sprite()

```lua
local sprite = Sprite(width, height [, colorMode])
local sprite = Sprite(spec)
local sprite = Sprite(otherSprite)
local sprite = Sprite{ fromFile=filename }
```

Creates a new sprite with the given `width` and `height`. The
[color mode](colormode.md) is optional, [RGB](colormode.md#colormodergb)
by default.

The `spec` parameter is an [image specification](imagespec.md) object.

If `otherSprite` is given (other `Sprite` object), the sprite is duplicated.

If `fromFile` is given, it indicates a file name (a string) and it's
like opening a new document with [`app.open()`](app.md#appopen).

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

## Sprite.selection

```lua
local selection = sprite.selection
sprite.selection = newSelection
```

Gets or sets the active sprite selection. This property is an instance
of the [Selection class](selection.md) to manipulate the set of
selected pixels in the canvas.

## Sprite.filename

```lua
local name = sprite.filename
sprite.filename = newName
```

Gets or sets the name of the file from where this sprite was loaded or
saved. Or an empty string if this is a new sprite without an
associated file.

## Sprite.colorMode

Returns the [color mode](colormode.md) of this sprite.

## Sprite.spec

```lua
local spec = sprite.spec
```

The [specification](imagespec.md) for image in this sprite.

## Sprite.frames

```lua
for i,frame in ipairs(s.frames) do
  -- ...
end
for i = 1,#s.frames do
  -- s.frames[i]
end
```

An array of [frames](frame.md).

## Sprite.palettes

An array of [palettes](palette.md). Generally it contains only one
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

An array of [layers](layer.md).

## Sprite.cels

```lua
for i,cel in ipairs(s.cels) do
  -- ...
end
for i = 1,#s.cels do
  -- s.cels[i]
end
```

An array of [cels](cel.md).

## Sprite.tags

```lua
for i,tag in ipairs(s.tags) do
  -- ...
end
for i = 1,#s.tags do
  -- s.tags[i]
end
```

An array of [tags](tag.md).

## Sprite.slices

```lua
for i,slice in ipairs(s.slices) do
  -- ...
end
for i = 1,#s.slices do
  -- s.slices[i]
end
```

An array of [slices](slice.md).

## Sprite.backgroundLayer

Returns the [background
layer](https://www.aseprite.org/docs/layers/#background-layer) a
[layer](layer.md) object or `nil` if the sprite doesn't contain a
background layer.

## Sprite.transparentColor

```lua
local number = sprite.transparentColor
sprite.transparentColor = number
```

The transparent color is an intenger that specifies what index (`0` by
default) is the transparent color in transparent layers on indexed
sprites.

## Sprite:resize()

```lua
sprite:resize(width, height)
sprite:resize(size)
```

Resize the sprite (and all frames/cels) to the given dimensions. See
[Size class](size.md).

## Sprite:crop()

```lua
sprite:crop(x, y, width, height)
sprite:crop(rectangle)
```

Crops the sprite to the given dimensions. See the
[Rectangle class](rectangle.md).

## Sprite:saveAs()

```lua
sprite:saveAs(filename)
```

Saves the sprite to the given file and mark the sprite as saved so
closing it doesn't will ask to save changes.

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

Changes the sprite [palette](palette.md).

## Sprite:assignColorSpace

```lua
local colorSpace = ColorSpace{ sRGB }
sprite:assignColorSpace(colorSpace)
```

Assign a new [color space](colorspace.md) to the sprite without
modifying the sprite pixels.

## Sprite:convertColorSpace

```lua
local colorSpace = ColorSpace{ sRGB }
sprite:convertColorSpace(colorSpace)
```

Converts all the sprite pixels to a new [color space](colorspace.md)
so the image looks the same as in the previous color space (all pixels
will be adjusted to the new color space).

## Sprite:newLayer()

```lua
local layer = sprite:newLayer()
```

Creates a new [layer](layer.md) at the top of the layers stack.

## Sprite:newGroup()

```lua
local layerGroup = sprite:newGroup()
```

Creates a new empty [layer group](layer.md) at the top of the layers stack.

## Sprite:deleteLayer()

```lua
sprite:deleteLayer(layer)
sprite:deleteLayer(layerName)
```

Deletes the given [layer](layer.md) or the layer with the given `layerName` (a string).

## Sprite:newFrame()

```lua
local frame = sprite:newFrame(frame)
local frame = sprite:newFrame(frameNumber)
```

Creates a copy of the given [frame](frame.md) object or frame number
and returns a [`Frame`](frame.md) that points to the newly created
frame in `frameNumber` position.

## Sprite:newEmptyFrame()

Creates a new empty frame in the given `frameNumber` (an integer) and
returns the new [frame](frame.md).

## Sprite:deleteFrame()

```lua
sprite:deleteFrame(frame)
```

## Sprite:newCel()

```lua
cel = sprite:newCel(layer, frame)
cel = sprite:newCel(layer, frame, image, position)
```

Creates a new [cel](cel.md) in the given [layer](layer.md) and `frame`
number. If the [image](image.md) is not specified, a new image will be
created with the size of the sprite canvas. The [position](point.md)
is a point to locate the image.

## Sprite:deleteCel()

```lua
sprite:deleteCel(cel)
sprite:deleteCel(layer, frame)
```

Deletes the given [cel](cel.md). If the cel is from a transparent
layer, the cel is completely deleted, but if the cel is from a
background layer, the cel will be delete with the
[background color](app.md#appbgcolor).

## Sprite:newTag()

```lua
local tag = sprite:newTag(fromFrameNumber, toFrameNumber)
```

Creates a new [tag](tag.md) in the given frame range and with the given name.

## Sprite:deleteTag()

```lua
sprite:deleteTag(tag)
sprite:deleteTag(tagName)
```

Deletes the given [tag](tag.md).

## Sprite:newSlice()

```lua
local slice = sprite:newSlice()
local slice = sprite:newSlice(Rectangle)
```

Returns a new [slice](slice.md).

## Sprite:deleteSlice()

```lua
sprite:deleteSlice(slice)
sprite:deleteSlice(sliceName)
```

Deletes the given [slice](slice.md).

## Sprite:flatten()

```lua
sprite:flatten()
```

Flatten all layers of the sprite into one layer.
It's like calling `app.commands.FlattenLayers()`.
