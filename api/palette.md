# Palette

## Palette()

```lua
local palette = Palette()
local palette = Palette(numberOfColors)
local palette = Palette(otherPalette)
local palette = Palette{ fromFile=filename }
```

Creates a new palette. By default it will contain 256 colors, but you
can specify a `numberOfColors` (integer value).

`otherPalette` can be another palette object to create a copy of it.

If `fromFile` is given, the palette is loaded from the file name.

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
