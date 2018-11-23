# Range

This class is used to represent the range of selected objects in the
timeline.

![Timeline Example](rangetype/cels.png)

It can be:

* A list of layers
* A list of frames
* A list of cels

Or a combination of those.

## Range.type

```lua
local type = range.type
```

Returns a [RangeType](rangetype.md).

## Range.isEmpty

```lua
local booleanResult = rectangle.isEmpty
```

Returns true if the range is empty, i.e. there is no selected range in
the timelin (a thick border in the timeline), only the [active cel](app.md#appactivecel)
in the sprite editor.

This is the same as asking for `range.type == RangeType.EMPTY`.

## Range.sprite

[Sprite](sprite.md#sprite) to which this range is pointing to.

## Range.layers

Returns an array of selected [layers](layer.md#layer).

## Range.frames

Returns an array of selected [frames](frame.md#frame).

## Range.cels

Returns an array of selected [cels](cel.md#cel).

## Range.images

Returns an array of selected [images](image.md#image) (images from linked
cels are counted just one time in this array).

## Range.editableImages

Returns an array of selected [images](image.md#image) in the range that are
in unlocked layers (editable).

## Range:contains()

```lua
local hasLayer = range:contains(layer)
local hasFrame = range:contains(frame)
local hasCel = range:contains(cel)
```

Returns true if the given object
([layer](layer.md#layer)/[frame](frame.md#frame)/[cel](cel.md#cel)) is
inside the selected range.
