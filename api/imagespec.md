# ImageSpec

It's a simple object that contains some specifications to create new
[sprites](sprite.md#sprite) or [images](image.md#image), or to get the
information (specs) of a [sprite](sprite.md#spritespec) or
[image](image.md#imagespec), like the canvas size (width/height),
[color mode](colormode.md#colormode), and color space. Often
abbreviated as 'spec' in the API.

## ImageSpec()

```lua
ImageSpec()
ImageSpec(otherImageSpec)
ImageSpec{
    width=number,
    height=number,
    colorMode=number,
    transparentColor=number }
```

Creates a new `ImageSpec` instance.

When no arguments are given, defaults to a width and height of 1, with
the transparent color index set to zero and RGB color mode.

## ImageSpec.colorMode

```lua
local colorMode = spec.colorMode
spec.colorMode = colorMode
```

Gets or sets the [color mode](colormode.md#colormode) of the image or
sprite.

## ImageSpec.width

```lua
local w = spec.width
spec.width = w
```

Gets or sets the width of the image or sprite.

## ImageSpec.height

```lua
local h = spec.height
spec.height = h
```

Gets or sets the height of the image or sprite.

## ImageSpec.colorSpace

```lua
local colorSpace = spec.colorSpace
spec.colorSpace = ColorSpace{ sRGB=true }
```

Gets or sets the [color space](colorspace.md#colorspace) for an image
or sprite.

## ImageSpec.transparentColor

```lua
local mask = spec.transparentColor
spec.transparentColor = mask
```

Gets or sets the index that refers a transparent color in a palette
when the image or sprite uses indexed [color mode](colormode.md#colormode).
