# Size

If a function receives a size as an argument it could be several things:

1. You can specify two parameters `width, height` directly as
   arguments of the function.
   E.g. `sprite:resize(64, 32)`
1. You can specify an object with `width` and `height` properties.
   E.g. `sprite:resize{ width=64, height=32 }`
1. You can specify an array two elements:
   E.g. `sprite:resize{ 64, 32 }`
1. You can specify a `Size` instance:
   E.g. `sprite:resize(Size(64, 32))`

## Size()

```lua
Size()
Size(otherSize)
Size(width, height)
Size{width=number, height=number}
Size{w=number, h=number}
Size{number, number}
```

Creates a new `Size` instance with the given dimensions (or
`width=height=0` if they are not specified).

## Size.width

```lua
local width = size.width
size.width = newWidth
```

## Size.height

```lua
local height = size.height
size.height = newHeight
```
## Size.w

Same as [Size.width](#sizewidth).

## Size.h

Same as [Size.height](#sizeheight).

## Size:union()

```lua
local newSize = size:union(otherSize)
```

Returns the new size `newSize` which will be big enough to contains
both given dimensions (`size` and `otherSize`).
