# Selection

## Selection()

```lua
Selection()
Selection(rectangle)
```

Creates a new empty selection, or with the given [rectangle](rectangle.md#rectangle).

## Selection.bounds

```lua
local rectangle = selection.bounds
```

Returns a [rectangle](rectangle.md#rectangle) with the bounds of the selection
(if the rectangle is empty, is because there is no selection).

## Selection.origin

```lua
local point = selection.origin
selection.origin = newPoint
```

Gets or sets the selection origin/position (a [point](point.md#point)).
This can be used to move the selection edges (not the content).

## Selection.isEmpty

```lua
local status = selection.isEmpty
```

Returns true if the selection is empty i.e. there are no pixels
selected.

## Selection:deselect()

```lua
selection:deselect()
```

## Selection:select()

```lua
selection:select(rectangle)
```

Replaces the selection with the given [rectangle](rectangle.md#rectangle).
If you want to add a rectangle to the selection, you can use [Selection:add()](selection.md#selectionadd).

## Selection:selectAll()

```lua
selection:selectAll()
```

Selected the whole sprite canvas. Only valid for a
[sprite.selection](sprite.md#spriteselection).

## Selection:add()

```lua
selection:add(rectangle)
selection:add(otherSelection)
```

Adds a new rectangle (or `otherSelection`) to the
`selection`. Creating an union between the existent selected area and
the given `rectangle`/`otherSelection`.

## Selection:subtract()

```lua
selection:subtract(rectangle)
selection:subtract(otherSelection)
```

Subtracts the given `rectangle` (or `otherSelection`) from `selection`.

## Selection:intersect()

```lua
selection:intersect(rectangle)
selection:intersect(otherSelection)
```

Creates an intersection in `selection` between the given `rectangle`
(or `otherSelection`) and the already selected area in `selection`.

## Selection:contains()

```lua
local status = selection:contains(point)
local status = selection:contains(x, y)
```

Returns true or false if the given [point](point.md#point) is inside the
selection.
