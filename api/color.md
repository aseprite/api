# Color

Represents a color that can be choose by the user in different kinds
(RGB, HSV, HSL, grayscale, indexed).

Don't confuse this color with the [app.pixelColor](pixelcolor.md#apppixelcolor)
which is used to put/get pixels to/from an [image](image.md#image).

## Color()

```lua
local c
c = Color{ r=255, g=255, b=255, a=255 }
c = Color{ h=360.0, s=1.0, v=1.0, a=255 }
c = Color{ h=360.0, s=1.0, l=1.0, a=255 }
c = Color{ red=255, green=255, blue=255, alpha=255 }
c = Color{ hue=360.0, saturation=1.0, value=1.0, alpha=255 }
c = Color{ hue=360.0, saturation=1.0, lightness=1.0, alpha=255 }
c = Color{ gray=255, alpha=255 }
c = Color{ index=integer }
c = Color(integer)
```

* If `alpha` argument is not specified, it's 255 by default (opacity = 100%).
* The `Color(integer)` constructor receives a [pixel color](pixelcolor.md#apppixelcolor)
  and the integer is interpreted depending on the [active sprite](app.md#appsprite).

## Color.alpha

```lua
local c = Color{ r=0, g=0, b=0, a=128 }
assert(c.alpha == 128)
```

## Color.red/green/blue

```lua
local c = Color{ r=255, g=128, b=32 }
assert(c.red   == 255)
assert(c.green == 128)
assert(c.blue  == 32)
c.red   = 20
c.green = 40
c.blue  = 255
```

Get/sets red/green/blue components of the color.

## Color.hsvHue/Saturation/Value

```lua
local c = Color{ h=45, s=0.5, v=0.2 }
assert(c.hsvHue        == 45)
assert(c.hsvSaturation == 0.5)
assert(c.hsvValue      == 0.2)
```

## Color.hslHue/Saturation/Lightness

## Color.hue

Gets/sets the [HSV hue](#colorhsvhuesaturationvalue) or [HSL hue](#colorhslhuesaturationlightness) depending on the kind of color.

## Color.saturation

Gets/sets the [HSV saturation](#colorhsvhuesaturationvalue) or [HSL saturation](#colorhslhuesaturationlightness) depending on the kind of color.

## Color.value

Gets/sets the [HSV value](#colorhsvhuesaturationvalue).

## Color.lightness

Gets/sets the [HSL lightness](#colorhslhuesaturationligthness).

## Color.index

```lua
local c = Color(index)
oldIndex = c.index
c.index = newIndex
```

Gets or sets the palette index related to this color. If the color is
not an index, i.e. it's RGB/HSL/HSV, the closest palette index of the
current palette (the palette of the active sprite) that matches the
RGB/HSL/HSV values will be returned.

## Color.gray

## Color.rgbaPixel

```lua
local c = Color{ r=200, g=100, b=0, a=255 }
assert(c.rgbaPixel == app.pixelColor.rgba(200, 100, 0, 255))
```

Returns the [pixel color](pixelcolor.md#apppixelcolorrgba) which is
equivalent to the RGBA values of this color.

## Color.grayPixel

Returns the [pixel color](pixelcolor.md#apppixelcolorgraya) which is
equivalent to the gray+alpha values of this color.
