# Frame

## Frame.sprite

```lua
local sprite = frame.sprite
```

Returns the [sprite](sprite.md) of this frame.

## Frame.frame

```lua
local frameNumber = frame.frame
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
