# app.pixelColor

The app.pixelColor namespace contains a set of functions to handle [image](image.md#image) pixels (colors) in the form of unsigned integers. The unsigned integer color format is used when pixels are handled directly (e.g: [`Image:putPixel()`](image.md#imageputpixel)), while the [Color](color.md#color) object is used for more high level applications (e.g: [`Layer.color`](layer.md#layercolor)). Unsigned integers are more efficient performance wise, so they are ideal for writing and reading pixels, as well as storing pixel data. 

Unsigned integers can represent different kinds of colors depending on the context:
  * [RGB](colormode.md#colormodergb) images: a `32-bit` unsigned integer value (8 bits for each of the four RGBA components)
  * [Gray](colormode.md#colormodegray) images: a `16-bit` unsigned integer with Alpha and Grayscale value (8 bits for Alpha, 8 bits for Gray)
  * [Indexed](colormode.md#colormodeindexed) images: an `8-bit` unsigned
   integer which represents a [palette index](palette.md#palettegetcolor), a value from `0` to `255`
  * [Tiles](tile.md#tile): a `32-bit` unsigned integer which represents a tile's index in a tileset and its [flipping flags](#apppixelcolortile_xfliptile_yfliptile_dflip). The first 3 bits are the tile's flipping flags (X, Y, and Diagonal), and the last 29 bits are the tile index.

Not to be confused with the [Color](color.md#color) object.

## app.pixelColor.rgba()

```lua
local rgbaPixelValue = app.pixelColor.rgba(red, green, blue [, alpha])
```

Constructs a `32-bit` unsigned integer for [RGBA](colormode.md#colormodergb) images.
Alpha will be `255` (i.e. `100%` opaque) if it's not specified.

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

Returns the red component of the given `32-bit` integer (`rgbaPixelValue`).
This integer is a value created with [`app.pixelColor.rgba()`](#apppixelcolorrgba)
or [`Image:getPixel()`](image.md#imagegetpixel) from a
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

Constructs a `16-bit` unsigned integer for [grayscale](colormode.md#colormodegrayscale) images.
Alpha will be `255` (i.e. `100%` opaque) if it's not specified.

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

Returns the gray component of the given `16-bit` integer (`grayPixelValue`).
This integer is a value created with [`app.pixelColor.graya()`](#apppixelcolorgraya)
or [`Image:getPixel()`](image.md#imagegetpixel) from a [grayscale](colormode.md#colormodegray) image.

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

## app.pixelColor.tile()

```lua
local tileValue = app.pixelColor.tile(index [, flags])
```

Constructs a `32-bit` unsigned integer for [Tiles](colormode.md#colormodergb). The first 3 bits are the tile's flipping flags (X, Y, and Diagonal), and the last 29 bits are the tile index. `index` is a tile's index in a [tileset](tileset.md#tileset) (integer), and `flags` is an integer that represents the tile's [flipping flags](#apppixelcolortile_xfliptile_yfliptile_dflip).

Example:

```lua
local pc = app.pixelColor
local x = app.pixelColor.TILE_XFLIP
local y = app.pixelColor.TILE_YFLIP
local d = 0
local index = 1
local tileValue = pc.tile(index, x|y|d)
-- the tile's index in the tileset is 1, and the tile is flipped in the x and y axes
-- binary value: 1100 0000 0000 0000 0000 0000 0000 0001
```
## app.pixelColor.tileI()

```lua
local index = app.pixelColor.tileI(tileValue)
```

Returns the [tileset](tileset.md#tileset) index of the given `32-bit` integer (`tileValue`), a value created with [`app.pixelColor.tile()`](#apppixelcolortile).

Example:

```lua
local pc = app.pixelColor
local tileValue = pc.tile(2)
local index = pc.tileI(tileValue)
-- index is 2
```

## app.pixelColor.tileF()

```lua
local flags = app.pixelColor.tileF(tileValue)
```

Returns the [flags integer](#apppixelcolortile_xfliptile_yfliptile_dflip) of the given `32-bit` integer (`tileValue`), a value created with [`app.pixelColor.tile()`](#apppixelcolortile).

Example:

```lua
local pc = app.pixelColor
local x = app.pixelColor.TILE_XFLIP
local d = app.pixelColor.TILE_DFLIP
local tileValue = pc.tile(1, x|d)
local flags = pc.tileF(tileValue)
-- flags is app.pixelColor.TILE_XFLIP|app.pixelColor.TILE_DFLIP
```

## app.pixelColor.TILE_XFLIP/TILE_YFLIP/TILE_DFLIP

Flipping flag unsigned integer constants for use with [`app.pixelColor.tile()`](#apppixelcolortile). `TILE_XFLIP` is for X flipping, `TILE_YFLIP` is for Y flipping, and `TILE_DFLIP` is for diagonal flipping. 

The first 3 bits of a tile unsigned integer are the tile's flipping flags: X, Y, and Diagonal. To set these bits, we can use the [bitwise OR operator](https://en.wikipedia.org/wiki/Bitwise_operation#OR) (`|`) (bit masking). Constructing a flags integer will look something like this:

```lua
local x = 0
local y = app.pixelColor.TILE_YFLIP
local d = app.pixelColor.TILE_DFLIP

local flagsInt = x|y|d
-- binary value of flagsInt: 0110 0000 0000 0000 0000 0000 0000 0000 
```
`flagsInt` has `y` and `d` set, while `x` is `0`; this means that a subsequent tile will be flipped on the Y and diagonal axis, but not the X axis.