# ColorSpace

Represents the [color space/profile](https://www.aseprite.org/docs/color-profile/)
of a [sprite](sprite.md#sprite), [image](image.md#image), or [image spec](imagespec.md#imagespec).

## ColorSpace()

```lua
local none = ColorSpace()
local srgb = ColorSpace{ sRGB=true }
local icc = ColorSpace{ fromFile="/path/file.icc" }
```

Creates an empty color space, sRGB color space, or loads a color
profile from the given ICC file specified in `fromFile` parameter.

## ColorSpace.name

```lua
local cs = ColorSpace()
local colorSpaceName = cs.name
```

Get/sets the color space name.
