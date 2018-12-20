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

## From v1.2.10-beta4 to v1.2.10

* [`app.apiVersion`](api/app.md#appapiversion) is `3`
* Added [`sprite:close()`](api/sprite.md#spriteclose) function
* Now [`sprite:saveAs()`](api/sprite.md#spritesaveas) changes the state of the
  sprite as a saved document

## From v1.2.10-beta3 to v1.2.10-beta4

* [`app.apiVersion`](api/app.md#appapiversion) is `2`
* Fixed [`app.sprites`](api/app.md#appsprites) table
* Added [`app.param`](api/app.md#appparam) table

## From v1.2.10-beta2 to v1.2.10-beta3

* [`app`](api/app.md#app)
  * New [`app.apiVersion`](api/app.md#appapiversion) with value `1`.
  * Different return value for `app.activeFrame`: Now it returns a
    [`Frame`](api/frame.md) instead of a frame number (an integer
    value). In v1.2.10-beta2 this function returned `nil` when we were
    in the first frame, now it returns the valid `Frame` object with
    `frame.frameNumber = 1`. You can access the old frame number value doing:
    ```lua
    local activeFrameNumber = app.activeFrame.frameNumber
    ```
  * New [`app.range`](api/app.md#apprange)
* [`Site`](api/site.md#frame)
  * Different return value for `app.site.frame`: Now it returns a
    [`Frame`](api/frame.md) instead of a frame number.
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

## v1.2.10-beta1 and v1.2.10-beta2

* [`app`](api/app.md#app)
  * `app.apiVersion` didn't exist (is `nil`)
