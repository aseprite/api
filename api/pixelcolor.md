# pixelColor

This is a property from [app](app.md) which contains functions to
handle color at the lowest level: a 32-bit unsigned integer.

This color format is used when you handle pixels with
[Image.getPixel](image.md#Image.getPixel) or
[Image.putPixel](image.md#Image.putPixel).

## pixelColor.rgba

    var color = app.pixelColor.rgba(red, green, blue, [, alpha])

Construct a RGBA color.

Example:

    var pc = app.pixelColor
    var red = pc.rgba(255, 0, 0)
    var semiTransparentWhite = pc.rgba(255, 255, 255, 128)

## pixelColor.rgbaR

    var redValue = app.pixelColor.rgbaR(color)

Returns the red component of the given pixel color.

Example:

    var pc = app.pixelColor
    var red = pc.rgbaG(pc.rgba(255, 128, 0))
    // red is 255

## pixelColor.rgbaG

Same as [rgbaR](#pixelColor.rgbaR) but with the Green component.

## pixelColor.rgbaB

Same as [rgbaR](#pixelColor.rgbaR) but with the Blue component.

## pixelColor.rgbaA

Same as [rgbaR](#pixelColor.rgbaR) but with the Alpha component.

## pixelColor.graya

    var color = app.pixelColor.graya(value [, alpha])

Construct a color for a grayscale [image](image.md).

Example:

    var pc = app.pixelColor
    var black = pc.graya(0)
    var white = pc.graya(255)
    var semiTransparentWhite = pc.graya(255, 128)

## pixelColor.grayaG

    var gray = app.pixelColor.grayaG(color)

Returns the gray component of the given pixel color.

Example:

    var pc = app.pixelColor
    var gray = pc.grayaG(pc.graya(128, 0))
    // gray is 128

## pixelColor.grayaA

Same as [grayaG](#pixelColor.grayaG) but with the Alpha component.
