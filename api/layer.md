# Layer

Layers are arranged as a stack within a sprite. Layers may nest within each other to form a hierarchy. Layers that accept children are group layers.

A layer can be created with [Sprite:newLayer](sprite.md#spritenewlayer). A group layer can be created with [Sprite:newGroup](sprite.md#spritenewgroup). Layers can be removed with [Sprite:deleteLayer](sprite.md#spritedeletelayer).

## Layer.blendMode

```lua
local blendMode = layer.blendMode
layer.blendMode = newBlendMode
```

Gets or sets the layer [BlendMode](blendmode.md#blendmode), expressed as an integer or enumerated constant.

## Layer.cels

Gets a `table` of [cels](cel.md#cel) in the layer. If the layer is a group, this property will return a table of zero length.

See also the [Layer:cel()](#layercel) method.

## Layer.color

```lua
local color = layer.color
layer.color = color
```

Gets or sets the user-defined [color](color.md#color) of this layer in the timeline.

## Layer.data

```lua
local data = layer.data
layer.data = data
```

Gets or sets the user-defined data related to this layer, a `string`.

## Layer.isBackground

Gets whether or not a layer is a background. The opposite of the property [Layer.isTransparent](#layeristransparent). Background layers do not contain images which support transparency. 

For context, see the general documentation on [layers](https://www.aseprite.org/docs/layers). 

## Layer.isCollapsed

Gets or sets whether or not a [group](#layerisgroup) layer is collapsed, i.e., whether its child layers are hidden in the timeline. The opposite of the property [Layer.isExpanded](#layerisexpanded).

The getter describes only the group layer's local collapse, not whether any hierarchy that contains it is collapsed. See [Layer.isVisible](#layerisvisible) for an example snippet using a similar property.

## Layer.isContinuous

Gets or sets whether a layer biases toward linked [cels](cel.md#cel) when a new cel is created in the timeline.

For context, see the general documentation on [continuous layers](https://www.aseprite.org/docs/continuous-layers/).

## Layer.isEditable

Gets or sets whether a layer is editable, unlocked in other words.

The getter describes only the group layer's local editability, not whether any hierarchy that contains it is editable. See [Layer.isVisible](#layerisvisible) for an example snippet using a similar property.

## Layer.isExpanded

Gets or sets whether or not a [group](#layerisgroup) layer is expanded, meaning whether its child layers are visible in the timeline. The opposite of the property [Layer.isCollapsed](#layeriscollapsed).

The getter describes only the group layer's local expansion, not whether any hierarchy that contains it is expanded. See [Layer.isVisible](#layerisvisible) for an example snippet using a similar property.

## Layer.isGroup

Gets whether or not the layer is a group and *has the capacity* to be a parent to other layers. A layer may be a group, yet have no children; in such a case, its [layers](#layerlayers) property will return a table of zero length.

Groups may nest within groups, creating a hierarchy.

## Layer.isImage

Gets whether or not the layer contains [cels](cel.md#cel) with [images](image.md#image).

## Layer.isReference

```lua
local isRef = layer.isReference
```

Gets whether or not the layer is a reference layer.

## Layer.isTransparent

Gets whether or not a layer supports transparency. The opposite of the property [Layer.isBackground](#layerisbackground). For [indexed color mode](colormode.md#colormodeindexed), the layer may contain images with a [transparent color](imagespec.md#imagespectransparentcolor) index. For RGB or grayscale color mode, the layer may contain images with an alpha channel.

For context, see the general documentation on [layers](https://www.aseprite.org/docs/layers).

## Layer.isVisible

Gets or sets whether or not the layer is visible.

```lua
local sprite = app.activeSprite
local layerGroup = sprite:newGroup()
local layers = sprite.layers
local layer1 = layers[1]
layer1.parent = layerGroup
layerGroup.isVisible = false
layer1.isVisible = true
print(layer1.isVisible)
```

The getter describes only the layer's local visibility, not its visibility with respect to any hierarchy that contains it.

## Layer.layers

If a layer is a [group](#layerisgroup), gets the `table` of child layers for which the group serves as a [parent](#layerparent). If the layer is not a group, returns `nil`.

## Layer.name

Gets or sets the layer name, a `string`.

## Layer.opacity

```lua
local opacity = layer.opacity
layer.opacity = newOpacity
```

Gets or sets the layer opacity, a value from `0` to `255`. The layer is completely transparent when the value is `0`; opaque when the value is `255`. When the layer is a [background](#layerisbackground), returns `255`. When the layer is a [group](#layerisgroup), returns `nil`.

## Layer.parent

Gets or sets the layer's parent. The parent may be either a [sprite](sprite.md#sprite) or layer that is a [group](#layerisgroup).

```lua
local spriteOrLayerGroup = layer.parent
layer.parent = sprite
layer.parent = group
```

Upon setting the parent, the child layer is moved to the top of the parent's layer [stack](#layerstackindex). Throws an error if the parent layer is not a group or if the setter tries to parent a layer to itself.

## Layer.sprite

Gets the [sprite](sprite.md#sprite) to which a layer belongs.

## Layer.stackIndex

```lua
local index = layer.stackIndex
layer.stackIndex = newPosition
```

Gets or sets the layer's index in its parent's layers `table`. In other words, this is the layer's place in the local stack. Layers stack in descending order. For example, a layer with index `1` will lie beneath a layer with index `2`, assuming the layers share the same parent.

## Layer:cel()

```lua
local cel = layer:cel(frameNumber)
assert(cel == layer:cel(sprite.frames[frameNumber]))
```

Returns a [cel](cel.md#cel), if any, at the intersection of the layer and a frame. The frame may be either a [frame](frame.md#frame) object or its [frame number](frame.md#frameframenumber), an integer. If there is no cel at that intersection, returns `nil`.