# Point

If a function receives a point as an argument it could be several things:

1. You can specify two parameters `x, y` directly as arguments of the
   function.  E.g. `selection:contains(8, 20)`
1. You can specify an object with `x` and `y` properties.
   E.g. `selection:contains{ x=8, y=20 }`
1. You can specify an array with two elements:
   E.g. `selection:contains{ 8, 20 }`
1. You can specify a `Point` instance:
   E.g. `selection:contains(Point(8, 20))`

## Point()

```lua
Point()
Point(otherPoint)
Point(x, y)
Point{x=number, y=number}
Point{number, number}
```

Creates a new `Point` instance with the given coordinates (or `x=y=0`
if they are not specified).

## Point.x

```lua
local x = point.x
point.x = newX
```

## Point.y

```lua
local y = point.y
point.y = newY
```
