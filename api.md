# API

There is one global object available, the `app` object that is an
instance of [Application][application.md] class.

* Globals
  * [rgba](#rgba)
  * [rgbaR, rgbaG, rgbaB, rgbaA](#rgbar-rgbag-rgbab-rgbaa)
  * [activeSprite](#activesprite)
* Classes
  * [Sprite](sprite.md)

# Globals

## rgba

    rgba(red, green, blue, [, alpha])

Construct a RGBA color.

Example:

    var red = rgba(255, 0, 0)
    var transparentWhite = rgba(255, 255, 255, 128)

## rgbaR, rgbaG, rgbaB, rgbaA

    var r = rgbaR(color)
    var g = rgbaG(color)
    var b = rgbaB(color)
    var a = rgbaA(color)

Returns the red, green, blue, or alpha components.

Example:

    var g = rgbaG(rgba(255, 128, 0))
    // g is 128

## activeSprite

    var sprite = activeSprite

Returns the active sprite, a [Sprite](sprite.md) object:
