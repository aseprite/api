# GraphicsContext

```lua
Dialog():canvas{
  onpaint = function(ev)
    local ctx = ev.context
    -- ctx is a GraphicsContext
  end
}
```

## GraphicsContext.width

Gets the width of the visible area in pixels.

## GraphicsContext.height

Gets the height of the visible area in pixels.

## GraphicsContext.antialias

It's true or false in case that you want to paint paths using
antialiasing.

## GraphicsContext.color

```lua
local color = gc.color
gc.color = Color(255)
```

Gets or sets the [color](color.md#color) to paint with the path functions.

## GraphicsContext.strokeWidth

## GraphicsContext:save()

```lua
gc:save()
```

Saves current clipping information to
[restore](#graphicscontextrestore) it later.

## GraphicsContext:restore()

```lua
gc:restore()
```

## GraphicsContext:clip()

```lua
gc:clip()
```

Sets the [current path](#graphicscontextbeginpath) as a clipping area
for following drawing operations.

## GraphicsContext:strokeRect()

```lua
gc:strokeRect(rectangle)
```

Paints the edges of the given [rectangle](rectangle.md#rectangle) with
the [current color](#graphicscontextcolor).

## GraphicsContext:fillRect()

```lua
gc:fillRect(rectangle)
```

Fills the given [rectangle](rectangle.md#rectangle) with the
[current color](#graphicscontextcolor).

## GraphicsContext:fillText()

```lua
gc:fillText(string, x, y)
```

## GraphicsContext:measureText()

```lua
local size = gc:measureText(string)
```

Returns the [size](size.md#size) of the text using the current font.

## GraphicsContext:drawImage()

```lua
gc:drawImage(image, x, y)
gc:drawImage(image, srcRect, dstRect)
gc:drawImage(image, srcX, srcY, srcW, srcH, dstX, dstY, dstW, dstH)
```

## GraphicsContext:drawThemeImage()

```lua
gc:drawThemeImage(partId, point)
gc:drawThemeImage(partId, x, y)
```

## GraphicsContext:drawThemeRect()

```lua
gc:drawThemeRect(partId, rectangle)
gc:drawThemeRect(partId, x, y, w, h)
```

## GraphicsContext:beginPath()

```lua
gc:beginPath()
```

## GraphicsContext:closePath()

```lua
gc:closePath()
```

## GraphicsContext:moveTo()

```lua
gc:moveTo(x, y)
```

## GraphicsContext:lineTo()

```lua
gc:lineTo(x, y)
```

## GraphicsContext:cubicTo()

```lua
gc:cubicTo(cp1x, cp1y, cp2x, cp2y, x, y)
```

## GraphicsContext:rect()

```lua
gc:rect(rectangle)
```

## GraphicsContext:roundedRect()

```lua
gc:roundedRect(rectangle, rx, ry)
```

## GraphicsContext:stroke()

```lua
gc:stroke()
```

Paints the edges of the [current path](#graphicscontextbeginpath) with
the [current color](#graphicscontextcolor).

## GraphicsContext:fill()

```lua
gc:fill()
```

Fills the [current path](#graphicscontextbeginpath) with the [current
color](#graphicscontextcolor).
