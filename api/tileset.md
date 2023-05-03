# Tileset

## Tileset.name

## Tileset.grid

## Tileset.baseIndex

## Tileset.color

## Tileset.data

## Tileset.properties

Access user-defined and extension-defined
[properties](properties.md#properties) of this tileset.

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
