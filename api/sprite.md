# Sprite

## Sprite.width

```lua
local w = sprite.width
sprite.width = w
```

Returns or changes the sprite width. Use
[Sprite.resize](#spriteresize) if you want to change the sprite size
resizing layers, images, etc.

## Sprite.height

```lua
local h = sprite.height
sprite.height = h
```

Returns or changes the sprite height. Use
[Sprite.resize](#spriteresize) if you want to change the sprite size
resizing layers, images, etc.

## Sprite.selection

The `sprite.selection` property is an instance of the
[Selection class](selection.md) to manipulate the set of selected
pixels in the canvas.

## Sprite.filename

The file from where this sprite was loaded or saved. Or an empty
string if this is a new sprite without an associated file.

## Sprite.colorMode

Returns the [color mode](colormode.md) of this sprite.

## Sprite:resize()

```lua
sprite:resize(width, height)
sprite:resize(size)
```

Resize the sprite (and all frames/cels) to the given dimensions. See
[Size class](size.md).

## Sprite:crop()

```lua
sprite:crop(x, y, width, height)
sprite:crop(rectangle)
```

Crops the sprite to the given dimensions. See the
[Rectangle class](rectangle.md).

## Sprite:save()

```lua
sprite:save()
```

## Sprite:saveAs()

```lua
sprite:saveAs(filename)
```

## Sprite:saveCopyAs()

```lua
sprite:saveCopyAs(filename)
```

## Sprite:loadPalette()

```lua
sprite:loadPalette(filename)
```
