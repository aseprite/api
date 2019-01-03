# ColorSpace

Represents the [color space/profile](https://www.aseprite.org/docs/color-profile/)
of a [sprite](sprite.md), [image](image.md), or [image spec](imagespec.md).

## ColorSpace()

```lua
local none = ColorSpace()
local srgb = ColorSpace{ sRGB }
local icc = ColorSpace{ filename="/path/file.icc" }
```

Creates an empty color space, sRGB color space, or loads a color
profile from the given ICC file in `filename`.

## ColorSpace.name

```lua
local cs = ColorSpace()
local colorSpaceName = cs.name
```

Get/sets the color space name.
