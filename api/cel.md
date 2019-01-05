# Cel

A [cel](https://www.aseprite.org/docs/cel/) is an [image](#celimage) in a specific
[*xy*-coordinate](#celposition), and a specific
[layer](#cellayer)/[frame](#celframe) combination.

## Cel.sprite

```lua
local sprite = cel.sprite
```

Cels belong to one [sprite](sprite.md). This property returns that sprite.

## Cel.layer

```lua
local layer = cel.layer
```

Returns the [layer](layer.md) where this cel is located.

## Cel.frame

```lua
local frame = cel.frame
```

Returns the [frame](frame.md#frame) object which this cel belongs.

## Cel.frameNumber

```lua
local frameNumber = cel.frameNumber
```

Returns the frame number which this cel belongs, the frame number `1`
is the first frame (not `0`).

## Cel.image

```lua
local image = cel.image
cel.image = newImage
```

Gets or sets the [image](image.md) with the pixels of this cel. This
is the preferred way to replace the cel image, because it generates
only one undoable action.

## Cel.bounds

```lua
local bounds = cel.bounds
```

Returns the [rectangle](rectangle.md) with the cel bounds (position
and size).

## Cel.position

```lua
local position = cel.position
cel.position = newPosition
```

Gets or sets the cel position.

## Cel.opacity

```lua
local opacity = cel.opacity
cel.opacity = newOpacity
```

Gets or sets the cel opacity. A value from `0` to `255` (which means
`0=0%` completely transparent, or `255=100%` completely opaque).

## Cel.color

```lua
local color = cel.color
cel.color = newColor
```

Gets or sets the user-defined [color](color.md) of this cel in the timeline.

## Cel.data

```lua
local data = cel.data
cel.data = newData
```

Gets or sets the user-defined data related to this cel (a text string).
