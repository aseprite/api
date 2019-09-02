# API Changes

We will try minimize API changes between versions and keep backward
compatibility, but if a function in the API was introduced with a bug,
it's probable that its behavior will change in the next Aseprite
release.

Deprecated should be avoided because might be removed in future
versions of Aseprite.

## Detect available API

You can use [`app.apiVersion`](api/app.md#appapiversion):

```lua
if app.apiVersion == nil then
  -- First scripting API available
  app.alert("This is Aseprite v1.2.10-beta1 or v1.2.10-beta2")
elseif app.apiVersion == 1 then
  -- Second revision of the scripting API
  app.alert("This is Aseprite v1.2.10-beta3")
else
  -- Future versions will be 2, 3, etc.
end
```

## v1.2.14

* [`app.apiVersion`](api/app.md#appapiversion) is `5`
* Added filter commands:
  * [`app.command.BrightnessContrast()`](api/command/BrightnessContrast.md#brightnesscontrast)
  * [`app.command.ColorCurve()`](api/command/ColorCurve.md#colorcurve)
  * [`app.command.ConvolutionMatrix()`](api/command/ConvolutionMatrix.md#convolutionmatrix)
  * [`app.command.Despeckle()`](api/command/Despeckle.md#despeckle)
  * [`app.command.HueSaturation()`](api/command/HueSaturation.md#huesaturation)
  * [`app.command.InvertColor()`](api/command/InvertColor.md#invertcolor)
  * [`app.command.Outline()`](api/command/Outline.md#outline)
  * [`app.command.ReplaceColor()`](api/command/ReplaceColor.md#replacecolor)
* New types:
  * [`FilterChannels`](api/filterchannels.md#filterchannels)
* Added support to convert arrays of 2 or 4 integers into [points](api/point.md#point),
  [sizes](api/size.md#size), and [rectangles](api/rectangle.md#rectangle).
* Added [`Range.colors`](api/range.md#rangecolors) and
  [`Range.containsColor`](api/range.md#rangecontainscolor) members. And new
  commands [`CopyColors`](api/command/CopyColors.md#copycolors)/[`MoveColors`](api/command/MoveColors.md#movecolors).
* Added [`Image:resize()`](api/image.md#imageresize) function.
* Changed [`Sprite:resize()`](api/sprite.md#spriteresize) behavior:
  resizes the sprite and images (not only the canvas).

## v1.2.13

* [`app.apiVersion`](api/app.md#appapiversion) is `4`
* [`app.useTool()`](app.md#appusetool) now can be used inside a
  [`app.transaction()`](app.md#apptransaction)
  ([#18](https://github.com/aseprite/api/issues/18))
* New params for [`app.command.NewFile`](api/command/NewFile.md#newfile).

## v1.2.10

* [`app.apiVersion`](api/app.md#appapiversion) is `3`
* [`app.version`](api/app.md#appversion) is an [`Version`](api/version.md#version) object
* [`Sprite`](api/sprite.md#sprite)
  * Added [`sprite:close()`](api/sprite.md#spriteclose) function
  * Added [`sprite:assignColorSpace()`](api/sprite.md#spriteassigncolorspace)
    and [`sprite:convertColorSpace()`](api/sprite.md#spriteconvertcolorspace)
  * Now [`sprite:saveAs()`](api/sprite.md#spritesaveas) changes the state of the
    sprite as a saved document
  * Now you can set [`sprite.filename`](api/sprite.md#spritefilename) property
* New [`ColorSpace`](api/colorspace.md#colorspace) class.
* New `focus` property for [Dialog:button](api/dialog.md#dialogbutton)
  and [Dialog:entry](api/dialog.md#dialogentry).
* New parameters for [`ExportSpriteSheet`](api/command/ExportSpriteSheet.md#exportspritesheet).
* New [`app.useTool()`](app.md#appusetool),
  [`Brush`](api/brush.md#brush),
  [`Tool`](api/tool.md#tool) class.

## v1.2.10-beta4

* [`app.apiVersion`](api/app.md#appapiversion) is `2`
* Fixed [`app.sprites`](api/app.md#appsprites) table
* Added [`app.params`](api/app.md#appparams) table

## v1.2.10-beta3

* [`app`](api/app.md#app)
  * New [`app.apiVersion`](api/app.md#appapiversion) with value `1`.
  * Different return value for `app.activeFrame`: Now it returns a
    [`Frame`](api/frame.md#frame) instead of a frame number (an integer
    value). In v1.2.10-beta2 this function returned `nil` when we were
    in the first frame, now it returns the valid `Frame` object with
    `frame.frameNumber = 1`. You can access the old frame number value doing:
    ```lua
    local activeFrameNumber = app.activeFrame.frameNumber
    ```
  * New [`app.range`](api/app.md#apprange)
* [`Site`](api/site.md#frame)
  * Different return value for `app.site.frame`: Now it returns a
    [`Frame`](api/frame.md#frame) instead of a frame number.
* [`Rectangle`](api/rectangle.md#rectangle)
  * Added [`Rectangle.contains`](api/rectangle.md#rectanglecontains) function.
  * Added [`Rectangle.intersect`](api/rectangle.md#rectangleintersect) function.
  * Added [`Rectangle.intersects`](api/rectangle.md#rectangleintersects) function.
  * Added [`Rectangle.union`](api/rectangle.md#rectangleunion) function.
* [`Sprite`](api/sprite.md#sprite)
  * Added [`Sprite.bounds`](api/sprite.md#spritebounds) property.
  * Different [`Sprite:newFrame`](api/sprite.md#spritenewframe) and
  [`Sprite:newEmptyFrame`](api/sprite.md#spritenewemptyframe) behavior
  (check documentation and [issue #4](https://github.com/aseprite/api/issues/4#issuecomment-444874154)).
* [`Image`](api/image.md#image)
  * Added [`Image:clear()`](api/image.md#imageclear) function.
  * Added [`Image:isEqual`](api/image.md#imageisequal),
    [`Image:clear`](api/image.md#clear).
  * Added [`Image:drawPixel`](api/image.md#imagedrawpixel) as an alias for
    `Image:putPixel` (both functions will be available).
  * Deprecated ~~`Image:putImage`~~, replaced with
    [`Image:drawImage`](api/image.md#imagedrawimage).
  * Deprecated ~~`Image:putSprite`~~, replaced with
    [`Image:drawSprite`](api/image.md#imagedrawsprite). Also
    `Image:putSprite` wasn't working correctly for positions != `0,0`.
* [`ColorMode`](api/colormode.md#colormode):
  * Deprecated ~~`ColorMode.GRAYSCALE`~~, replaced with
    [`ColorMode.GRAY`](api/colormode.md#colormodegray).
* [`Tag`](api/tag.md#tag):
  * Different return value for
    [`Tag.fromFrame`](api/tag.md#tagfromframe) and
    [`Tag.toFrame`](api/tag.md#tagtoframe): now they return a [`Frame`](api/frame.md#frame)
    object instead of an integer value.
* All functions that receive an integer can automatically accept
  floating numbers doing an implicit `math.floor(number)` conversion.

## v1.2.10-beta2

* [`app`](api/app.md#app)
  * `app.apiVersion` didn't exist (is `nil`)
