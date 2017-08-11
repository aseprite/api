# Sprite

## Sprite.width

    var w = sprite.width

## Sprite.height

    var h = sprite.height

## Sprite.selection

The `sprite.selection` property is an instance of the
[Selection class](selection.md) to manipulate the set of selected
pixels in the canvas.

## Sprite.filename

The file from where this sprite was loaded or saved. Or an empty
string if this is a new sprite without an associated file.

## Sprite.colorMode

Returns the [color mode](colormode.md) of this sprite.

## Sprite.resize()

    sprite.resize(width, height)
    sprite.resize(size)

Resize the sprite (and all frames/cels) to the given dimensions. See
[Size class](size.md).

## Sprite.crop()

    sprite.crop(x, y, width, height)
    sprite.crop(rectangle)

Crops the sprite to the given dimensions. See the
[Rectangle class](rectangle.md).

## Sprite.save()

    sprite.save()

## Sprite.saveAs()

    sprite.saveAs(filename)

## Sprite.saveCopyAs()

    sprite.saveCopyAs(filename)

## Sprite.loadPalette()

    sprite.loadPalette(filename)
