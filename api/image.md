# Image

An image object. Each [cel](https://www.aseprite.org/docs/cel/) has
one image (all [linked cels](https://www.aseprite.org/docs/linked-cels/)
share the same image).

## Image()

```lua
local image = Image(width, height [, colorMode])
```

## Image:clone()

```lua
local copy = image:clone()
```

Creates a copy of the given image. The new image is unrelated to the
sprite, but can be used to update the image in a transaction. E.g. You
clone an image, modify the pixels from the copy, and then you
[patch the image](#imagepatch).

## Image.width

```lua
local w = image.width
```

## Image.height

```lua
local h = image.height
```

## Image:putPixel()

```lua
image:putPixel(x, y, color)
```

Sets the pixel in the *xy*-coordinate to the given
[pixel color](pixelcolor.md).

## Image:getPixel()

```lua
local color = image:getPixel(x, y)
```

Returns the [pixel color](pixelcolor.md) for the given *xy*-coordinate.
