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

## GraphicsContext.height

## GraphicsContext.antialias

## GraphicsContext.color

## GraphicsContext.strokeWidth

## GraphicsContext:save()

## GraphicsContext:restore()

## GraphicsContext:clip()

## GraphicsContext:strokeRect()

## GraphicsContext:fillRect()

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

## GraphicsContext:closePath()

## GraphicsContext:moveTo()

## GraphicsContext:lineTo()

## GraphicsContext:cubicTo()

## GraphicsContext:rect()

## GraphicsContext:roundedRect()

## GraphicsContext:stroke()

## GraphicsContext:fill()
