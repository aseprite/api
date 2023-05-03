# Rectangle

If a function receives a rectangle as an argument it could be several
things:

1. You can specify the parameters `x, y, width, height` directly as
   arguments of the function.
   E.g. `sprite:crop(0, 16, 64, 32)`
1. You can specify an object with `x`, `y`, `width`, and `height` properties.
   E.g. `sprite:crop{ x=0, y=16, width=64, height=32 }`
1. You can specify an array with 4 elements:
   E.g. `sprite:crop{ 0, 16, 64, 32 }`
1. You can specify a `Rectangle` instance:
   E.g. `sprite:crop(Rectangle(0, 16, 64, 32))`

## Rectangle()

```lua
Rectangle()
Rectangle(otherRectangle)
Rectangle(x, y, width, height)
Rectangle{x=number, y=number, width=number, height=number}
Rectangle{x=number, y=number, w=number, h=number}
Rectangle{number, number, number, number}
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

## Rectangle.w

Same as [Rectangle.width](#rectanglewidth).

## Rectangle.h

Same as [Rectangle.height](#rectangleheight).

## Rectangle.origin

```lua
local point = rectangle.origin
rectangle.origin = newPoint
```

Gets or sets the origin of the rectangle with a
[Point](point.md#point) object, just like changing
[Rectangle.x](#rectanglex) and [Rectangle.y](#rectangley) at the same
time.

## Rectangle.size

```lua
local size = rectangle.size
rectangle.size = newSize
```

Gets or sets the size of the rectangle with a [Size](size.md#size)
object, just like changing [Rectangle.width](#rectanglewidth) and
[Rectangle.height](#rectangleheight) at the same time.

## Rectangle.isEmpty

```lua
local booleanResult = rectangle.isEmpty
```

Returns true if the rectangle is empty i.e. [width](#rectanglewidth)
and/or [height](#rectangleheight) are 0.

## Rectangle:contains()

```lua
local booleanResult = rectangle:contains(otherRectangle)
```

Returns true if `otherRectangle` is inside `rectangle`.

Example:

```lua
local bounds = Rectangle{ x=0, y=0, width=32, height=32 }
local rectInside = Rectangle{ x=4, y=4, width=8, height=8 }
if bounds:contains(rectInside) then ... end
```

## Rectangle:intersects()

```lua
local booleanResult = rectangle:intersects(otherRectangle)
```

Returns true if `rectangle` intersects in some way `otherRectangle`.

## Rectangle:intersect()

```lua
local newRectangle = rectangle:intersect(otherRectangle)
```

Returns the new rectangle `newRectangle` which is the intersection of
`rectangle` and `otherRectangle`. If both rectangles don't intersect each other, the result will be an [empty rectangle](#rectangleisempty)

## Rectangle:union()

```lua
local newRectangle = rectangle:union(otherRectangle)
```

Returns the new rectangle `newRectangle` which will be a rectangle big
enough to contains both given rectangles `rectangle` and
`otherRectangle`.
