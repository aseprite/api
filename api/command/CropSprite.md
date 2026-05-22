# CropSprite

```lua
app.command.CropSprite {
  x=int,
  y=int,
  width=int,
  height=int
}
```

Crops the sprite to the given bounds.
All parameters default to 0. If none are given, the sprite will be cropped to the mask bounds.

* `x`: The X value of the crop bounds
* `y`: The Y value of the crop bounds
* `width`: The crop width
* `height`: The crop height
