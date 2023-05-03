# Tile

Represents a tile from a [Tileset](tileset.md#tileset).

## Tile.index

The index of the tile (position in its [tileset](tileset.md#tileset)).

## Tile.image

```lua
local image = tile.image
tile.image = newImage
```

Gets or sets the [image](image.md#image) of this tile.

## Tile.color

```lua
local color = tile.color
tile.color = newColor
```

Gets or sets the user-defined [color](color.md#color) of this tile.

## Tile.data

```lua
local data = tile.data
tile.data = newData
```

Gets or sets the user-defined data related to this tile (a text string).

## Tile.properties

Access user-defined and extension-defined
[properties](properties.md#properties) of this tile.
