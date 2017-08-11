# Selection

## new Selection()

    new Selection()
    new Selection(rectangle)

Creates a new empty selection, or with the given rectangle.

## Selection.bounds

    var rectangle = selection.bounds

Returns a [rectangle](rectangle.md) with the bounds of the selection
(if the rectangle is empty, is because there is no selection).

## Selection.deselect()

    selection.deselect()

## Selection.select()

    selection.select(rectangle)

Selects the given [rectangle](rectangle.md).

## Selection.selectAll()

    selection.selectAll()

Selected the whole sprite canvas. Only valid for a
[sprite.selection](sprite.md#spriteselection).
