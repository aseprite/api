# ChangePixelFormat

```lua
app.command.ChangePixelFormat {
  format=string,
  dithering=string,
  ["dithering-matrix"]=string,
  rgbmap=string,
  toGray=string
}
```

Changes the [ColorMode](../colormode.md) of the active [sprite](../sprite.md)

* `format`: Can be `"rgb"`, `"gray"`, or `"indexed"`.
* `dithering`: Can be `"ordered"`, `"old"` `"error-diffusion"`,
  or empty.
* `dithering-matrix`: It can be `"bayer8x8"`, `"bayer4x4"`, or `"bayer2x2"` (when When `dithering` is `ordered` or `old`).
  Actually it can be a matrix ID from any extensions ([for example](https://github.com/aseprite/aseprite/blob/fc79146c56f941f834f28809f0d2c4d7fd60076c/data/extensions/bayer-matrices/package.json#L8)).
* `rgmap`: `"octree"`, `"rgb5a3"`, or `"default"` (generally default
  will be octree, but it might change in the future). If nothing is
  specified the default configured quantization method from prefereces
  will be used if the GUI is enabled.
* `toGray`: `"luma"`, `"hsv"`, or `"hsl"`.

## Example

```lua
app.command.ChangePixelFormat {
  format="indexed"
}
```
