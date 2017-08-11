# app

The `app` global object.

## app.activeImage

    var image = app.activeImage

Returns the active image, an [Image](image.md) object.

## app.activeSprite

    var sprite = app.activeSprite

Returns the active sprite, a [Sprite](sprite.md) object.

## app.pixelColor

This [pixelColor object](pixelcolor.md) contains internal functions to
handle color at the lowest level.

## app.version

Returns the Aseprite version number as a string (e.g. `"1.2-beta12"`).

## app.open()

    app.open(filename)

Opens a new sprite loading it from the given filename. Returns an
instance of the [Sprite class](sprite.md) or `null` if something went
wrong.

## app.exit()

    app.exit()

Closes the application. It's like clicking *File > Exit* menu option.
