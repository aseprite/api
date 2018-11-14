# API Changes

We will try minimize API changes between versions and keep backward
compatibility, but if a function in the API was introduced with a bug,
it's probable that its behavior will change in the next Aseprite
release.

Deprecated should be avoided because might be removed in future
versions of Aseprite.

## From v1.2.10-beta2 to v1.2.10-beta3

* Added [`Image:clear()`](api/image.md#imageclear) function.

* Different return value for `app.activeFrame`: Now it returns a
  [`Frame`](api/frame.md) instead of a frame number (an integer
  value). In v1.2.10-beta2 this function returned `nil` when we were
  in the first frame, now it returns the valid `Frame` object with
  `frame.frameNumber = 1`. You can access the old frame number value doing:
  ```lua
  local activeFrameNumber = app.activeFrame.frameNumber
  ```

* Added [`Image:drawPixel`](api/image.md#imagedrawpixel) as an alias for
  `Image:putPixel` (both functions will be available).

* Deprecated ~~`Image:putImage`~~, replaced with
  [`Image:drawImage`](api/image.md#imagedrawimage).

* Deprecated ~~`Image:putSprite`~~, replaced with
  [`Image:drawSprite`](api/image.md#imagedrawsprite). Also
  `Image:putSprite` wasn't working correctly for positions != `0,0`.

* Deprecated ~~`ColorMode.GRAYSCALE`~~, replaced with
  [`ColorMode.GRAY`](api/colormode.md#colormodegray).
