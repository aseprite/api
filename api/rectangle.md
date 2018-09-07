# Rectangle

If a function receives a rectangle as an argument it could be several
things:

1. You can specify the parameters `x, y, width, height` directly as
   arguments of the function.
   E.g. `sprite:crop(0, 16, 64, 32)`
1. You can specify an object with `x`, `y`, `width`, and `height` properties.
   E.g. `sprite:crop{ x=0, y=16, width=64, height=32 }`
1. You can specify a `Rectangle` instance:
   E.g. `sprite:crop(Rectangle(0, 16, 64, 32))`

## Rectangle()

```lua
Rectangle()
Rectangle(otherRectangle)
Rectangle(x, y, width, height)
Rectangle{x=number, y=number, width=number, height=number}
```

## Rectangle.x

```lua
local x = rectangle.x
rectangle.x = newX
```

Gets or sets the *x*-coordinate of the rectangle. 0 means at the left
side of the screen/sprite.

## Rectangle.y

```lua
local y = rectangle.y
rectangle.y = newY
```

Gets or sets the *y*-coordinate of the rectangle. 0 means at the top side
of the screen/sprite.

## Rectangle.width

```lua
local width = rectangle.width
rectangle.width = newWidth
```

Gets or sets the *width* of the rectangle. If it's 0, the rectangle is
empty (so the coordinate doesn't matter).

## Rectangle.height

```lua
local height = rectangle.height
rectangle.height = newHeight
```

Gets or sets the *height* of the rectangle. If it's 0, the rectangle is
empty (so the coordinate doesn't matter).

## Rectangle.isEmpty

```lua
local status = rectangle.isEmpty
```

Returns true if the rectangle is empty i.e. [width](#rectanglewidth)
and/or [height](#rectangleheight) are 0.
