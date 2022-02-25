# ImageSpec

An object that contains specifications for a [sprite](sprite.md#sprite) or an [image](image.md#image). Includes width and height, color mode and color space. Often abbreviated to 'spec' in the API.

## ImageSpec()

```lua
ImageSpec()
ImageSpec(otherImageSpec)
ImageSpec{
    colorMode=number,
    height=number,
    transparentColor=number,
    width=number }
```

Creates a new `ImageSpec` instance.

The copy constructor allows a sprite's specification to be passed to an image. Use with named parameters when instantiating from `number`s. When no arguments are given, defaults to a width and height of 1, with the transparent color index set to zero and RGB color mode.

## ImageSpec.colorMode

```lua
local colorMode = spec.colorMode
spec.colorMode = colorMode
```

Gets or sets the [color mode](colormode.md#colormode) of the image or sprite.

## ImageSpec.colorSpace

```lua
local colorSpace = spec.colorSpace
spec.colorSpace = ColorSpace{ sRGB=true }
```

Gets or sets the [color space](colorspace.md#colorspace) for an image or sprite.

## ImageSpec.height

```lua
local h = spec.height
spec.height = h
```

Gets or sets the height of the image or sprite.

## ImageSpec.transparentColor

```lua
local mask = spec.transparentColor
spec.transparentColor = mask
```

Gets or sets the index that refers a transparent color in a palette when the image or sprite uses indexed [color mode](colormode.md#colormode).

## ImageSpec.width

```lua
local w = spec.width
spec.width = w
```

Gets or sets the width of the image or sprite.