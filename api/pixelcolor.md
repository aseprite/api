# app.pixelColor

This [`app`](app.md#app) property contains a set of function to handle the color
for [Image pixels](image.md#imagepixels) at the lowest level: an unsigned integer.

On Aseprite there are two kind of ways to handle colors:

1. The [Color](color.md#color) object type (a high-level/abstract/user-friendly way to handle color)
2. Or an unsigned integer (low-level/performance-wise) value which can represent several kind of colors:
   - For [RGB](colormode.md#colormodergb) images: a 32-bit unsigned integer value (8-bit for each of the four RGBA component)
   - [Gray](colormode.md#colormodegray) images: a 16-bit unsigned integer with Alpha and Grayscale value (8-bit for Alpha, 8-bit for Gray)
   - [Indexed](colormode.md#colormodeindexed) images: 8-bit unsigned
     integer which represents a value from 0 to 255 to reference a
     [palette entry](palette.md#palettegetcolor)

For performance reasons, pixel values on [images](image.md#image) are
handled with the second kind of colors: an unsigned integer value.
This color format is used when you handle pixels directly with functions like
[Image:getPixel()](image.md#imagegetpixel),
[Image:putPixel()](image.md#imageputpixel), or
[Image:pixels()](image.md#imagepixels).

## app.pixelColor.rgba()

```lua
local rgbaPixelValue = app.pixelColor.rgba(red, green, blue, [, alpha])
```

Constructs a 32-bit unsigned integer for [RGBA](colormode.md#colormodergb) images.
Alpha will be 255 (i.e. 100% opaque) if it's not specified.

Example:

```lua
local pc = app.pixelColor
local redPixel = pc.rgba(255, 0, 0)
local semiTransparentWhite = pc.rgba(255, 255, 255, 128)
```

## app.pixelColor.rgbaR()

```lua
local redComponent = app.pixelColor.rgbaR(rgbaPixelValue)
```

Returns the red component of the given 32-bit integer (`rgbaPixelValue`).
This integer is a value created with [`app.pixelColor.rgba()`](apppixelcolorrgba)
or [`Image:getPixel()`]() from a
[RGBA](colormode.md#colormodergb) image.

Note: RGB components **are not** premultiplied by alpha.

Example:

```lua
local pc = app.pixelColor
local rgbaPixelValue = pc.rgba(255, 128, 0)
local redComponent = pc.rgbaR(rgbaPixelValue)
local greenComponent = pc.rgbaG(rgbaPixelValue)
-- redComponent is 255
-- greenComponent is 128
```

## app.pixelColor.rgbaG()

Same as [rgbaR()](#apppixelcolorrgbar) but with the Green component.

## app.pixelColor.rgbaB()

Same as [rgbaR()](#apppixelcolorrgbar) but with the Blue component.

## app.pixelColor.rgbaA()

Same as [rgbaR()](#apppixelcolorrgbar) but with the Alpha component.

## app.pixelColor.graya()

```lua
local grayPixelValue = app.pixelColor.graya(gray [, alpha])
```

Constructs a 16-bit unsigned integer for [grayscale](colormode.md#colormodegrayscale) images.
Alpha will be 255 (i.e. 100% opaque) if it's not specified.

Example:

```lua
local pc = app.pixelColor
local black = pc.graya(0)
local white = pc.graya(255)
local semiTransparentWhite = pc.graya(255, 128)
```

## app.pixelColor.grayaV()

```lua
local grayValue = app.pixelColor.grayaV(grayPixelValue)
```

Returns the gray component of the given 16-bit integer (`grayPixelValue`).
This integer is a value created with [`app.pixelColor.graya()`](apppixelcolorgraya)
or [`Image:getPixel()`]() from a [grayscale](colormode.md#colormodegray) image.

Example:

```lua
local pc = app.pixelColor
local grayPixelValue = pc.graya(128, 32)
local grayComponent = pc.grayaV(grayPixelValue)
local alphaComponent = pc.grayaA(grayPixelValue)
-- grayComponent is 128
-- alphaComponent is 32
```

## app.pixelColor.grayaA()

Same as [grayaV()](#apppixelcolorgrayav) but with the Alpha component.
