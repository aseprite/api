# Tag

## Tag.sprite

## Tag.fromFrame

Returns the first [`Frame`](frame.md#frame) object where this tag starts.

Note: Old versions (Aseprite v1.2.10-beta2) returned a frame number
instead of a `Frame` object.

## Tag.toFrame

Returns the last [`Frame`](frame.md#frame) object where this tag ends.

Note: Old versions (Aseprite v1.2.10-beta2) returned a frame number
instead of a `Frame` object.

## Tag.frames

Returns the number of frames that this tag contain. Equal to:

```lua
local frames = tag.toFrame.frameNumber - tag.fromFrame.frameNumber + 1
```

## Tag.name

## Tag.aniDir

## Tag.color

```lua
local color = tag.color
tag.color = color
```

Gets or sets the user-defined [color](color.md#color) of this tag in the timeline.
