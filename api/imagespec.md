# ImageSpec

It's a simple structure that contains some specifications of a
[sprite](sprite.md#sprite) or [image](image.md#image) (like canvas size,
[color mode](colormode.md#colormode), etc.)

## ImageSpec.colorMode

```lua
local colorMode = spec.colorMode
spec.colorMode = colorMode
```

The [color mode](colormode.md#colormode) of the image.

## ImageSpec.width

```lua
local w = spec.width
spec.width = w
```

Canvas width.

## ImageSpec.height

```lua
local h = spec.height
spec.height = h
```

Canvas height.

## ImageSpec.transparentColor

```lua
local mask = spec.transparentColor
spec.transparentColor = mask
```

Index in the palette that represent the transparent color in
transparent layers in indexed sprites.
