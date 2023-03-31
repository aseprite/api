# ColorMode

The color mode of an sprite or image specifies the internal structure
of each pixel. You can see the [Color Mode section in the Aseprite docs](https://www.aseprite.org/docs/color-mode/)
for an introduction about each color mode.

## ColorMode.RGB

You can use this color mode to create RGBA
[sprites](sprite.md#sprite) and [images](image.md#image).

Each pixel is a 32-bit unsigned integer where each component (Red,
Green, Blue, and Alpha) uses 8-bit (values from 0 to 255).

## ColorMode.GRAY

You can use this color mode to create gray
[sprites](sprite.md#sprite) and [images](image.md#image).
Known as `ColorMode.GRAYSCALE` in previous versions.

Each pixel is a 16-bit unsigned integer where each component (Gray and
Alpha) uses 8-bit (values from 0 to 255).

## ColorMode.INDEXED

You can use this color mode to create indexed
[sprites](sprite.md#sprite) and [images](image.md#image).

Each pixel is an 8-bit unsigned integer (a value from 0 to 255) which
indicates the specific [palette entry](palette.md#palettesetcolor) which
the pixel refers.

## ColorMode.TILEMAP

Special color mode used for tilemaps, where each pixel is tile
reference in a [tileset](tileset.md#tileset).
