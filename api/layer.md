# Layer

## Layer.sprite

Gets the sprite to which this layer belongs.

## Layer.name

Gets/sets the layer name (a string).

## Layer.opacity

Gets/sets the layer opacity value (an integer value from `0` to `255`).

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
