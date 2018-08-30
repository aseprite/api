# Image

An image object. Each [cel](https://www.aseprite.org/docs/cel/) has
one image (all [linked cels](https://www.aseprite.org/docs/linked-cels/)
share the same image).

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
