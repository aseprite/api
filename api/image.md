# Image

An image object. Each [cel](https://www.aseprite.org/docs/cel/) has
one image (all [linked cels](https://www.aseprite.org/docs/linked-cels/)
share the same image).

## Image()

```lua
local image = Image(width, height [, colorMode])
local image = Image(spec)
```

Creates a new image with the given `width` and `height`. The
[color mode](colormode.md) is optional, [RGB](colormode.md#colormodergb)
by default.

The `spec` parameter is an [image specification](imagespec.md) object.

## Image:clone()

```lua
local copy = image:clone()
```

Creates a copy of the given image. The new image is unrelated to the
sprite, but can be used to update the image in a transaction. E.g. You
clone an image, modify the pixels from the copy, and then you
[patch the image](#imageputimage).

## Image.width

```lua
local w = image.width
```

## Image.height

```lua
local h = image.height
```

## Image.colorMode

```lua
local colorMode = image.colorMode
```

Image [color mode](colormode.md).

## Image.spec

```lua
local spec = image.spec
```

The [specification](imagespec.md) for this image.

## Image:putPixel()

```lua
image:putPixel(x, y, color)
```

Sets the pixel in the *xy*-coordinate to the given
[pixel color](pixelcolor.md).

**Warning**: This method doesn't create undo information, you should
[clone the image](#imageclone) and then [patch it](#imageputimage) to
get proper undo/redo information.

## Image:getPixel()

```lua
local color = image:getPixel(x, y)
```

Returns the [pixel color](pixelcolor.md) for the given *xy*-coordinate.

## Image:putImage()

```lua
destinationImage:putImage(sourceImage [, position ] )
```

Copies/draws the given *sourceImage* image over *destinationImage*.
If *position* is a [point](point.md), it will put the given image in
the given position.

**Warning**: This method generates undo information, so you could use
it as an individual operation or in a [transaction](app.md#apptransaction).

## Image:pixels()

```lua
iterator = image:pixels()
iterator = image:pixels(rectangle)
```

Returns a pixel iterator for the whole image or the given
[rectangle](rectangle.md). Then you can use the iterator in these
ways:

```lua
for it in image:pixels() do
  local pixelValue = it() -- get pixel
  it(pixelValue)          -- set pixel
  print(it.x, it.y)       -- get pixel x,y coordinates
end
```

A `pixelValue` can be interpreted with the
[app.pixelColor](pixelcolor.md) functions.
