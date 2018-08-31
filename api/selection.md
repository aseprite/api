# Selection

## Selection()

```lua
Selection()
Selection(rectangle)
```

Creates a new empty selection, or with the given [rectangle](rectangle.md).

## Selection.bounds

```lua
local rectangle = selection.bounds
```

Returns a [rectangle](rectangle.md) with the bounds of the selection
(if the rectangle is empty, is because there is no selection).

## Selection:deselect()

```lua
selection:deselect()
```

## Selection:select()

```lua
selection:select(rectangle)
```

Selects the given [rectangle](rectangle.md).

## Selection:selectAll()

```lua
selection:selectAll()
```

Selected the whole sprite canvas. Only valid for a
[sprite.selection](sprite.md#spriteselection).

## Selection:contains()

```lua
local status = selection:contains(point)
local status = selection:contains(x, y)
```

Returns true or false if the given [point](point.md) is inside the
selection.
