# Grid

An object that defines the grid for a [tileset](tileset.md#tileset).

## Grid()

```lua
Grid()
Grid(otherGrid)
```

Creates a new grid object. If `otherGrid` is defined, the constructor will make a copy.

## Grid.tileSize

```lua 
local tileSize = grid.tileSize
```

Returns the [tile](tile.md#tile) width and height of a [tileset](tileset.md#tileset), as a [size](size.md#size).

## Grid.origin

```lua 
local point = grid.origin
```

Returns the origin of the grid as a [point](point.md#point).