# app.pixelColor

This [`app`](app.md#app) property contains functions to handle low-level
[pixel values](image.md#imagepixels) as unsigned integers. Depending on
the image's [color mode](colormode.md#colormode), these values represent
colors or tilemap entries.

On Aseprite there are two ways to handle colors:

1. The [Color](color.md#color) object type (a high-level/abstract/user-friendly way to handle color)
2. An unsigned integer (low-level/performance-wise) value which can represent several kinds of colors:
   - For [RGB](colormode.md#colormodergb) images: a 32-bit unsigned integer value (8-bit for each of the four RGBA components)
   - [Gray](colormode.md#colormodegray) images: a 16-bit unsigned integer with Alpha and Grayscale value (8-bit for Alpha, 8-bit for Gray)
   - [Indexed](colormode.md#colormodeindexed) images: 8-bit unsigned
     integer which represents a value from 0 to 255 to reference a
     [palette entry](palette.md#palettegetcolor)

For performance reasons, pixel values on [images](image.md#image) are
handled as unsigned integers. This representation is used when you
handle pixels directly with functions like
[Image:getPixel()](image.md#imagegetpixel),
[Image:putPixel()](image.md#imageputpixel), or
[Image:pixels()](image.md#imagepixels).

For [tilemap images](colormode.md#colormodetilemap), each pixel is a
32-bit unsigned integer containing a tile index and flip flags instead
of a color. Use [`tile()`](#apppixelcolortile),
[`tileI()`](#apppixelcolortilei), and [`tileF()`](#apppixelcolortilef)
to compose and decompose these tilemap entries.

## app.pixelColor.rgba()

```lua
local rgbaPixelValue = app.pixelColor.rgba(red, green, blue [, alpha])
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
local tilePixelValue = app.pixelColor.tile(tileIndex [, tileFlags])
```

Constructs a 32-bit unsigned integer for a
[tilemap image](colormode.md#colormodetilemap). The low 29 bits contain
the tile index (`0x1fffffff` mask), and the high 3 bits contain the
[flip flags](#tile-flags) (`0xe0000000` mask). Bits outside each
argument's mask are discarded. If `tileFlags` is omitted, it is `0`
(no flips).

The index refers to a tile in the tilemap
[layer's tileset](layer.md#layertileset): `0` is the empty tile, and `1`
is the first user-defined tile. This function only encodes the value;
it does not create a tile or check whether the index exists in a tileset.

Example:

```lua
local pc = app.pixelColor
local tilePixelValue = pc.tile(5, pc.TILE_XFLIP | pc.TILE_YFLIP)
-- tilePixelValue is 0xc0000005 (tile 5, flipped horizontally and vertically)
local tileIndex = pc.tileI(tilePixelValue) -- 5
local tileFlags = pc.tileF(tilePixelValue) -- 0xc0000000
assert(pc.tile(tileIndex, tileFlags) == tilePixelValue)
```

## app.pixelColor.tileI()

```lua
local tileIndex = app.pixelColor.tileI(tilePixelValue)
```

Returns the tile index with all flip flags removed, equivalent to
`tilePixelValue & 0x1fffffff`. The value can come from
[`tile()`](#apppixelcolortile),
[`Image:getPixel()`](image.md#imagegetpixel), or
[`Image:pixels()`](image.md#imagepixels) on a tilemap image.

Use this index with [`Tileset:tile()`](tileset.md#tilesettile) to get
the tile. Its [image](tile.md#tileimage) contains the original pixels;
the entry's flags describe how that tile is displayed in this cel.

## app.pixelColor.tileF()

```lua
local tileFlags = app.pixelColor.tileF(tilePixelValue)
```

Returns just the flip flags, equivalent to
`tilePixelValue & 0xe0000000`. The bits remain in their original high
positions; the result is not shifted down to a number from 0 to 7.
It is `0` when no flags are set.

Use bitwise AND (`&`) to test a flag and bitwise OR (`|`) to combine
flags. Compare each test with `0`: in Lua, even `0` is true in a
condition.

This example reads every entry of the active tilemap cel, including
its position in tile coordinates relative to the cel image:

```lua
local pc = app.pixelColor
local cel = app.cel
assert(cel and cel.layer.isTilemap, "Select a tilemap cel")
local tileset = cel.layer.tileset

for pixel in cel.image:pixels() do
  local tilePixelValue = pixel()
  local tileIndex = pc.tileI(tilePixelValue)
  local flags = pc.tileF(tilePixelValue)
  local xFlip = (flags & pc.TILE_XFLIP) ~= 0
  local yFlip = (flags & pc.TILE_YFLIP) ~= 0
  local dFlip = (flags & pc.TILE_DFLIP) ~= 0

  if tileIndex ~= 0 then
    local tile = tileset:tile(tileIndex)
    print(pixel.x, pixel.y, tile.index, xFlip, yFlip, dFlip)
  end
end
```

## app.pixelColor.TILE_XFLIP

`0x80000000`: Flips the tile horizontally (left to right).
See [Tile flags](#tile-flags) for combinations with the other flags.

## app.pixelColor.TILE_YFLIP

`0x40000000`: Flips the tile vertically (top to bottom).
See [Tile flags](#tile-flags) for combinations with the other flags.

## app.pixelColor.TILE_DFLIP

`0x20000000`: Flips the tile diagonally by swapping its x and y axes.
For a square tile, this reflects across the top-left to bottom-right
diagonal, exchanging the top-right and bottom-left corners. The
diagonal flip is intended for square tiles; on non-square tiles
Aseprite clips the swap to the smaller of the tile's width and height.
See [Tile flags](#tile-flags) for the order of transformations.

## Tile flags

Flags describe the orientation of a tilemap entry without modifying
the tile's image in the tileset. Different cels can refer to the same
tile index with different flags.

To transform the original tile into its displayed orientation, apply
the diagonal flip first, then the horizontal and vertical flips.
Horizontal and vertical flips can be applied in either order, but
moving the diagonal flip after them changes the result. If you render
by looking up a source pixel for each destination pixel, reverse this
order: undo the horizontal and vertical flips, then swap x and y.

For example, take a square tile with corners labeled `1 2` in its top row
and `3 4` in its bottom row. These are all eight possible orientations
(`X`, `Y`, and `D` stand for the corresponding constants above):

| Flags | Top row | Bottom row | Transformation |
| --- | --- | --- | --- |
| `0` | `1 2` | `3 4` | Unchanged |
| `X` | `2 1` | `4 3` | Horizontal flip |
| `Y` | `3 4` | `1 2` | Vertical flip |
| `X \| Y` | `4 3` | `2 1` | 180-degree rotation |
| `D` | `1 3` | `2 4` | Diagonal flip |
| `D \| X` | `3 1` | `4 2` | 90-degree clockwise rotation |
| `D \| Y` | `2 4` | `1 3` | 90-degree counterclockwise rotation |
| `D \| X \| Y` | `4 2` | `3 1` | Reflection across the other diagonal |

This follows the same flip order as
[Tiled's orthogonal/isometric tile flags](https://doc.mapeditor.org/en/stable/reference/global-tile-ids/#tile-flipping).
When exporting, map the extracted tile index to the destination
format's tile IDs separately: Aseprite indices are local to the layer's
tileset, while Tiled uses global tile IDs. Aseprite uses only three
flag bits; `0x10000000` is part of the Aseprite tile index, not Tiled's
additional hexagonal rotation flag.
