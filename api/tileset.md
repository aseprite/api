# Tileset

A set of [tiles](tile.md#tile).

## Tileset.name

```lua
local name = tileset.name
tileset.name = name
```

Gets or sets the name of this tileset.

## Tileset.baseIndex

```lua
local baseindex = tileset.baseIndex
tileset.baseIndex = baseindex
```

Gets or sets the base index of this tileset.

## Tileset.color

## Tileset.data

```lua
local data = tileset.data
tileset.data = data
```

Gets or sets the user-defined data related to this tileset (a text string).

## Tileset.properties

Access user-defined and extension-defined
[properties](properties.md#properties) of this tileset.

## Tileset.grid

```lua
local grid = tileset.grid
```

Returns the [grid](grid.md#grid) of this tileset.

## Tileset:tile()

```lua
local tile = ts:tile(index)
```

Returns the [tile](tile.md#tile) in the given index (`0` is the empty
tile, so `1` is the first user-defined tile).

## Tileset:getTile()

```lua
local tileImage = ts:getTile(index)
```

Returns the image of tile in the given index (`0` is the empty tile,
so `1` is the first user-defined tile).

Note: This method was superseded with [Tileset:tile()](#tilesettile),
so you can use the following alternative:

```lua
local tileImage = ts:tile(index).image
```
