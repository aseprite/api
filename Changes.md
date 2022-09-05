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

## v1.2.40 & v1.3-beta21

* [`app.apiVersion`](api/app.md#appapiversion) is `20`
* Added [app.range.slices](api/range.md#rangeslices) object
* Only in v1.3-beta21:
  * Added `bounds` parameter to [app.command.SaveFileCopyAs](command/SaveFile.md#savefile) command
  * Added `splitGrid` & `fromTilesets` parameters to [app.command.ExportSpriteSheet](command/ExportSpriteSheet.md#exportspritesheet) command

## v1.2.36

* [`app.apiVersion`](api/app.md#appapiversion) is `19`
* Fixed several issues with [app.command.SaveFile/SaveFileAs/SaveFileCopyAs](command/SaveFile.md#savefile) commands
* Fixed [Sprite:newSlice](api/sprite.md#spritenewslice), now it adds undo information

## v1.2.35

* [`app.apiVersion`](api/app.md#appapiversion) is `18`
* Now `Dialog()` returns `nil` if we are running in `-batch` mode
* New `Cel.frame`/`Cel.frameNumber` setters
* Comparing `Layer`s with `Sprite`s just return false [#3218](https://github.com/aseprite/aseprite/issues/3218)

## v1.2.33

* [`app.apiVersion`](api/app.md#appapiversion) is `17`
* New `Color{ index }`
* Now `Color.index` returns an integer instead of a number

## v1.2.31

* [`app.apiVersion`](api/app.md#appapiversion) is `16`
* New `filenamechange` event for [`Sprite.events`](api/sprite.md#spriteevents)
* Possibility to change `options` field for [`Dialog:combobox()`](api/dialog.md#dialogcombobox) from [`Dialog:modify()`](api/dialog.md#dialogmodify)

## v1.2.30

* [`app.apiVersion`](api/app.md#appapiversion) is `15`
* New `onenabled` attribute for [`plugin:newCommand()`](api/plugin.md#pluginnewcommand)
* New [`App.events`](api/app.md#appevents) and [`Sprite.events`](api/sprite.md#spriteevents) properties, and [`Events`](api/events.md#events) class
* New [`Image.bytes`](api/image.md#imagebytes) and [`Image.rowStride`](api/image.md#imagerowstride) properties
* New [`WebSocket`](api/websocket.md#websocket) class and [`WebSocketMessageType`](api/websocketmessagetype.md#websocketmessagetype) constants
* New [`Layer.isReference`](api/layer.md#layerisreference) property

## v1.2.28

* [`app.apiVersion`](api/app.md#appapiversion) is `14`
* Added `selection` argument to
  [`app.useTool{}`](api/app.md#appusetool) to use selection tools
* New [`SelectionMode`](api/selectionmode.md#selectionmode)

## v1.2.26

* [`app.apiVersion`](api/app.md#appapiversion) is `13`
* New [`app.fs.makeDirectory`](api/app_fs.md#appfsmakedirectory)/[`app.fs.makeAllDirectories`](api/app_fs.md#appfsmakealldirectories)/[`app.fs.removeDirectory`](api/app_fs.md#appfsremovedirectory)
  functions to manipulate directories
* Added [`Sprite.pixelRatio`](api/sprite.md#spritepixelratio) property
* Added [`app.command.ImportSpriteSheet`](api/command/ImportSpriteSheet.md#importspritesheet).

## v1.2.22

* [`app.apiVersion`](api/app.md#appapiversion) is `12`
* New [`app.command.CanvasSize()`](api/command/CanvasSize.md#canvassize) params (`ui` and `bounds`)
* Fixed crash undoing `Sprite:newCel()` in background layer
* Fixed `Dialog onclose` event, now it's called when we close the app and the dialog is still opened [#28](https://github.com/aseprite/api/issues/28)
* API changes:
  * You must use `Dialog:newrow{ always=true }` to activate the automatic "newrow" (`Dialog:newrow{ always }` cannot be used)
  * You must use `ColorSpace{ sRGB=true }` to create an sRGB color space (`ColorSpace{ sRGB }` cannot be used)
  * Now [`app.command.SetInkType{ type=... }`](api/command/SetInkType.md#setinktype) works

## v1.2.19

* [`app.apiVersion`](api/app.md#appapiversion) is `11`
* Added support to modify more properties with [`Dialog:modify{}`](api/dialog.md#dialogmodify)
  ([PR#2359](https://github.com/aseprite/aseprite/pull/2359/commits/b3681fdbb0489d49333b3b5719fb79ddad504e95),
  separator text [#27](https://github.com/aseprite/api/issues/27))
* Added some extra `onchange` and `onrelease` events for some widgets like [`Dialog:slider{}`](api/dialog.md#dialogslider)
  ([PR#2359](https://github.com/aseprite/aseprite/pull/2359/commits/1311173d978d1619229dd6f5bf95dee016a37851))
* Added more arguments (`bgColor`, `ink`, `button`, `opacity`, `contiguous`, `tolerance`, `freehandAlgorithm`) to [`app.useTool{}`](api/app.md#appusetool)
* New [Ink](api/ink.md#ink) constants

## v1.2.18

* [`app.apiVersion`](api/app.md#appapiversion) is `10`
* New [`Tag.color`](api/tag.md#tagcolor) property
* New [`MouseButton`](api/mousebutton.md#mousebutton) which enumerates
  possible values for the new `ev.button` value of the
  [`Dialog:shades{ onclick }`](api/dialog.md#dialogshades) widget callback
* New [`Dialog:modify{}`](api/dialog.md#dialogmodify) method to change
  widget properties dynamically
* New [`Dialog:newrow{ always=true }`](api/dialog.md#dialognewrow) variant
* New [`Range:clear()`](api/range.md#rangeclear) function
* New [`Range.layers`](api/range.md#rangelayers) and [`Range.frames`](api/range.md#rangeframes) setters

## v1.2.17

* [`app.apiVersion`](api/app.md#appapiversion) is `9`
* New [`app.fs`](api/app_fs.md#appfs) with several functions to handle filenames and paths
* New [`Dialog{ onclose }`](api/dialog.md#dialog-1) constructor with a table with fields like `title` and `onclose`
* New [`Dialog:shades{}`](api/dialog.md#dialogshades) widget
* New [`Image:saveAs{ filename, palette }`](api/image.md#imagesaveas) function

## v1.2.16.3

* [`app.apiVersion`](api/app.md#appapiversion) is `8`
* Fixed [`Layer.stackIndex`](api/layer.md#layerstackindex) setter when
  the number we use is higher than the current `stackIndex` of the
  layer
* Now [`app.preferences.document(nil)`](api/app_preferences.md#apppreferencesdocument)
  returns the default preferences for documents

## v1.2.16

* [`app.apiVersion`](api/app.md#appapiversion) is `7`
* Added [`Sprite.gridBounds`](api/sprite.md#spritegridbounds) property

## v1.2.15

* [`app.apiVersion`](api/app.md#appapiversion) is `6`
* Fixed [`Sprite:resize()`](api/sprite.md#spriteresize): Now it can resize the non-active sprite.
* Fixed [`Sprite:newTag()`](api/sprite.md#spritenewtag): Adds undo
  information (can be used inside a transaction now).

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
* [`Sprite.layers`](api/sprite.md#spritelayers) returns only the first
  level of layers (in previous versions it returned all the layers,
  even sublayers inside groups).
* New [`Layer.layers`](api/layer.md#layerlayers) property to get the layer groups
* Possibility to change [`Layer.parent`](api/layer.md#layerparent) property
* New [`Layer.stackIndex`](api/layer.md#layerstackindex) property to reorder layers

## v1.2.13

* [`app.apiVersion`](api/app.md#appapiversion) is `4`
* [`app.useTool()`](api/app.md#appusetool) now can be used inside a
  [`app.transaction()`](api/app.md#apptransaction)
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
* New [`app.useTool()`](api/app.md#appusetool),
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
