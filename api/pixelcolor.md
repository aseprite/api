# PixelColor

This is a property from [app](app.md) which contains functions to
handle color at the lowest level: a 32-bit unsigned integer.

This color format is used when you handle pixels with
[Image.getPixel()](image.md#imagegetpixel) or
[Image.putPixel()](image.md#imageputpixel).

## PixelColor.rgba()

    var color = app.pixelColor.rgba(red, green, blue, [, alpha])

Construct a RGBA color.

Example:

    var pc = app.pixelColor
    var red = pc.rgba(255, 0, 0)
    var semiTransparentWhite = pc.rgba(255, 255, 255, 128)

## PixelColor.rgbaR()

    var redValue = app.pixelColor.rgbaR(color)

Returns the red component of the given pixel color.
The component **is not** premultiplied by alpha.

Example:

    var pc = app.pixelColor
    var red = pc.rgbaG(pc.rgba(255, 128, 0))
    // red is 255

## PixelColor.rgbaG()

Same as [rgbaR()](#pixelcolorrgbar) but with the Green component.

## PixelColor.rgbaB()

Same as [rgbaR()](#pixelcolorrgbar) but with the Blue component.

## PixelColor.rgbaA()

Same as [rgbaR()](#pixelcolorrgbar) but with the Alpha component.

## PixelColor.graya()

    var color = app.pixelColor.graya(value [, alpha])

Construct a color for a grayscale [image](image.md).

Example:

    var pc = app.pixelColor
    var black = pc.graya(0)
    var white = pc.graya(255)
    var semiTransparentWhite = pc.graya(255, 128)

## PixelColor.grayaG()

    var gray = app.pixelColor.grayaG(color)

Returns the gray component of the given pixel color.

Example:

    var pc = app.pixelColor
    var gray = pc.grayaG(pc.graya(128, 0))
    // gray is 128

## PixelColor.grayaA()

Same as [grayaG()](#pixelcolorgrayag) but with the Alpha component.
