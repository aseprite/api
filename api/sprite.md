# Sprite

## Sprite()

```lua
local sprite = Sprite(width, height [, colorMode])
```

Creates a new sprite with the given `width` and `height`. The
[color mode](colormode.md) is optional, [RGB](colormode.md#colormodergb)
by default.

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

## Sprite.selection

The `sprite.selection` property is an instance of the
[Selection class](selection.md) to manipulate the set of selected
pixels in the canvas.

## Sprite.filename

The file from where this sprite was loaded or saved. Or an empty
string if this is a new sprite without an associated file.

## Sprite.colorMode

Returns the [color mode](colormode.md) of this sprite.

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

## Sprite:saveCopyAs()

```lua
sprite:saveCopyAs(filename)
```

## Sprite:loadPalette()

```lua
sprite:loadPalette(filename)
```

## Sprite:setPalette()

```lua
sprite:setPalette(palette)
```

Changes the sprite [palette](palette.md).

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
sprite:newLayer(layer)
sprite:newLayer(layerName)
```

Deletes the given [layer](layer.md) or the layer with the given `layerName` (a string).

## Sprite:newFrame()

```lua
local frame = sprite:newFrame(frameNumber)
```

Creates a copy of the given `frameNumber` (an integer) and returns the
new [frame](frame.md).

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
