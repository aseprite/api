# Tag

Represents [a tag in the timeline](https://www.aseprite.org/docs/tags/).

## Tag.sprite

Returns the sprite to which this tag belongs.

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

```lua
local name = tag.name
tag.name = name
```

Gets or sets the name of the tag (a string).

## Tag.aniDir

```lua
local aniDir = tag.aniDir
tag.aniDir = AniDir.FORWARD
tag.aniDir = AniDir.REVERSE
tag.aniDir = AniDir.PING_PONG
```

Gets or sets the *[Animation Direction](https://www.aseprite.org/docs/tags/)* property of the tag.

## Tag.color

```lua
local color = tag.color
tag.color = color
```

Gets or sets the user-defined [color](color.md#color) of this tag in the timeline.

## Tag.data

```lua
local data = tag.data
tag.data = data
```

Gets or sets the user-defined data related to this tag, a `string`.
