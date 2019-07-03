# Palette

## Palette()

```lua
local palette = Palette()
local palette = Palette(numberOfColors)
local palette = Palette(otherPalette)
local palette = Palette{ fromFile=filename }
local palette = Palette{ fromResource=resourceID }
```

Creates a new palette. By default it will contain 256 colors, but you
can specify a `numberOfColors` (integer value).

`otherPalette` can be another palette object to create a copy of it.

If `fromFile` is given, the palette is loaded from the file name.

If `fromResource` is given, the `resourceID` is an ID specified in one
of the [extensions
palette](https://github.com/aseprite/aseprite/tree/master/data/extensions)
(e.g.
[`DB16`](https://github.com/aseprite/aseprite/blob/8e193b592ae06abb36be6f72ef43c308b511b24c/data/extensions/dawnbringer-palettes/package.json#L13),
[`DB32`](https://github.com/aseprite/aseprite/blob/8e193b592ae06abb36be6f72ef43c308b511b24c/data/extensions/dawnbringer-palettes/package.json#L14),
[`Solarized`](https://github.com/aseprite/aseprite/blob/8e193b592ae06abb36be6f72ef43c308b511b24c/data/extensions/software-palettes/package.json#L15)).

## Palette:resize()

```lua
palette:resize(ncolors)
```

Changes the number of the palette colors to `ncolors` (an integer
value).

## Palette:getColor()

## Palette:setColor()

## Palette.frame

## Palette:saveAs()

```lua
palette:saveAs(filename)
```

Saves the palette in the given `filename`.
