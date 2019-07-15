# Frame

This is an auxiliary object that points to a given frame in the sprite
and can be used to adjust information about that frame. If you modify
the number of frames in the sprite, or the structure of the frames, a
`Frame` object will still pointing to the same frame number.

## Frame.sprite

```lua
local sprite = frame.sprite
```

Returns the [sprite](sprite.md#sprite) of this frame.

## Frame.frameNumber

```lua
local frameNumber = frame.frameNumber
```

Returns the frame number. `1` is the first frame in the animation and
this `frame` is equal to `frame == frame.sprite.frames[frameNumber]`.

## Frame.duration

```lua
local duration = frame.duration
frame.duration = duration
```

Gets or sets the duration of this frame in the animation in
seconds. E.g. `0.3333` means that this frame will be `1/3` of a second
in the screen when the animation is being played.

## Frame.previous

Returns `Frame` object in the previous frame number or `nil` if this
is the first frame.

## Frame.next

Returns `Frame` object in the next frame number or `nil` if this is
the last frame.
