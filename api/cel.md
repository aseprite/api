# Cel

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

Returns the frame number, `1` is the first frame (not `0`).

## Cel.image

```lua
local image = cel.image
```

Returns the [image](image.md) with the pixels of this cel.

## Cel.bounds

```lua
local bounds = cel.bounds
```

Returns the [rectangle](rectangle.md) with the cel bounds (position
and size).

## Cel.position

```lua
local position = cel.position
cel.position = position
```

Gets or sets the cel position.

## Cel.opacity

```lua
local opacity = cel.opacity
cel.opacity = opacity
```

Gets or sets the cel opacity. A value from `0` to `255`.

## Cel.color

```lua
local color = cel.color
cel.color = color
```

Gets or sets the user-defined [color](color.md) of this cel in the timeline.

## Cel.data

```lua
local data = cel.data
cel.data = data
```

Gets or sets the user-defined data related to this cel (a text string).
