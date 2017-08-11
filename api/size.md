# Size

If a function receives a size as an argument it could be several things:

1. You can specify the parameter `width, height` directly as
   arguments of the function.
   E.g. `sprite.resize(64, 32)`
1. You can specify an object with `width` and `height` properties.
   E.g. `sprite.resize({ 'width': 64, 'height': 32 })`
1. You can specify a `Size` instance:
   E.g. `sprite.resize(new Size(64, 32))`

## new Size()

    new Size()
    new Size(otherSize)
    new Size(width, height)
    new Size({ 'width': number, 'height': number })

Creates a new `Size` instance with the given dimensions (or
`width=height=0` if they are not specified).

## Size.width

    var width = size.width
    size.width = newWidth

## Size.height

    var height = size.height
    size.height = newHeight
