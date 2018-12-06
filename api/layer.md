# Layer

## Layer.sprite

Gets the sprite to which this layer belongs.

## Layer.name

Gets/sets the layer name (a string).

## Layer.opacity

```lua
local opacity = layer.opacity
layer.opacity = newOpacity
```

Gets or sets the cel opacity. A value from `0` to `255` (which means
`0=0%` completely transparent, or `255=100%` completely opaque).

## Layer.isImage

Is true if this image has [cels](cel.md) with [images](image.md).

## Layer.isGroup

Is true if this image has sublayers inside.

## Layer.isTransparent

## Layer.isBackground

## Layer.isEditable

## Layer.isVisible

## Layer.isContinuous

## Layer.isCollapsed

## Layer.isExpanded

## Layer.cels

Returns the collection of [cels](cel.md) of this layer. Empty if the
layer is a group.

See also the [Layer:cel()](#layercel) function.

## Layer.color

```lua
local color = layer.color
layer.color = color
```

Gets or sets the user-defined [color](color.md) of this layer in the timeline.

## Layer.data

```lua
local data = layer.data
layer.data = data
```

Gets or sets the user-defined data related to this layer (a text string).

## Layer:cel()

```lua
local cel = layer:cel(frameNumber)
assert(cel == layer:cel(sprite.frames[frameNumber]))
```

Returns the [Cel](cel.md#cel) in the given [frame](frame.md#frame) or
`frameNumber` (an integer). Returns `nil` if there is no cel in the layer/frame.
