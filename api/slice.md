# Slice

An object that allows for [nine-slice scaling](https://en.wikipedia.org/wiki/9-slice_scaling). It can be created with the slice tool or with [Sprite:newSlice](sprite.md#spritenewslice).

## Slice.bounds

Gets or sets a slice's bounding [rectangle](rectangle.md#rectangle).

## Slice.center

Gets or sets the central [rectangle](rectangle.md#rectangle) of a slice's nine-slice. The getter returns `nil` when nine-slicing is inactive in Aseprite's user interface. The rectangle's top-left corner is defined in local coordinates.

```lua
local sliceBounds = slice.bounds
local inset = 3
slice.center = Rectangle(
    inset, inset,
    sliceBounds.width - inset * 2,
    sliceBounds.height - inset * 2)
```

For example, the snippet above insets the central rectangle by three pixels.

## Slice.color

```lua
local color = slice.color
slice.color = color
```

Gets or sets the user-defined [color](color.md#color) of this slice in the timeline.

## Slice.data

```lua
local data = slice.data
slice.data = data
```

Gets or sets the user-defined data related to this slice, a `string`.

## Slice.properties

Access user-defined and extension-defined
[properties](properties.md#properties) of this slice.

## Slice.name

Gets or sets the a slice's name, a `string`.

## Slice.pivot

Gets or sets the slice's pivot, a [point](point.md#point). The getter returns `nil` when the pivot is inactive in Aseprite's user interface. The pivot is defined in local coordinates relative to the slice's top-left corner.

```lua
local sliceBounds = slice.bounds
slice.pivot = Point(
    sliceBounds.width // 2,
    sliceBounds.height // 2)
```

For example, the snippet above sets the pivot to the slice's approximate center.

## Slice.sprite

Gets the [sprite](sprite.md#sprite) to which a slice belongs.