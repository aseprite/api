# ChangePixelFormat

```lua
app.command.ChangePixelFormat {
  format=string,
  dithering=string,
  ["dithering-matrix"]=string,
  rgbmap=string,
  toGray=string,
  fitCriteria=string
}
```

Changes the [ColorMode](../colormode.md) of the active [sprite](../sprite.md)

* `format`: `"rgb"`, `"gray"`, or `"indexed"`.
* `dithering`: Optional, `"ordered"`, `"old"` `"error-diffusion"`
* `dithering-matrix`: Optional, `"bayer8x8"`, `"bayer4x4"`, or `"bayer2x2"` (when When `dithering` is `ordered` or `old`).
  Actually it can be a matrix ID from any extension ([for example](https://github.com/aseprite/aseprite/blob/fc79146c56f941f834f28809f0d2c4d7fd60076c/data/extensions/bayer-matrices/package.json#L8)).
* `rgbmap`: Optional, `"octree"`, `"rgb5a3"`, or `"default"` (generally default
  will be octree, but it might change in the future). If nothing is
  specified the default configured quantization method from preferences
  will be used if the GUI is enabled.
* `toGray`: Optional, `"luma"`, `"hsv"`, or `"hsl"`.
* `fitCriteria`: Optional, `"rgb"`, `"linearizedRGB"`, `"ciexyz"`, `"cielab"`, or `"default"`

## Example

```lua
app.command.ChangePixelFormat {
  format="indexed"
}
```
