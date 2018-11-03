# PixelColor

This is a property from [app](app.md) which contains functions to
handle color at the lowest level: a 32-bit unsigned integer.

This color format is used when you handle pixels with
[Image:getPixel()](image.md#imagegetpixel) or
[Image:putPixel()](image.md#imageputpixel).

## PixelColor.rgba()

```lua
local color = app.pixelColor.rgba(red, green, blue, [, alpha])
```

Construct a RGBA color.

Example:

```lua
local pc = app.pixelColor
local red = pc.rgba(255, 0, 0)
local semiTransparentWhite = pc.rgba(255, 255, 255, 128)
```

## PixelColor.rgbaR()

```lua
local redValue = app.pixelColor.rgbaR(color)
```

Returns the red component of the given pixel color.
The component **is not** premultiplied by alpha.

Example:

```lua
var pc = app.pixelColor
var red = pc.rgbaG(pc.rgba(255, 128, 0))
-- red is 255
```

## PixelColor.rgbaG()

Same as [rgbaR()](#pixelcolorrgbar) but with the Green component.

## PixelColor.rgbaB()

Same as [rgbaR()](#pixelcolorrgbar) but with the Blue component.

## PixelColor.rgbaA()

Same as [rgbaR()](#pixelcolorrgbar) but with the Alpha component.

## PixelColor.graya()

```lua
local color = app.pixelColor.graya(value [, alpha])
```

Construct a color for a grayscale [image](image.md).

Example:

```lua
local pc = app.pixelColor
local black = pc.graya(0)
local white = pc.graya(255)
local semiTransparentWhite = pc.graya(255, 128)
```

## PixelColor.grayaV()

```lua
local gray = app.pixelColor.grayaV(color)
```

Returns the value component of the given gray pixel.

Example:

```lua
local pc = app.pixelColor
local gray = pc.grayaV(pc.graya(128, 0))
-- gray is 128
```

## PixelColor.grayaA()

Same as [grayaV()](#pixelcolorgrayav) but with the Alpha component.
