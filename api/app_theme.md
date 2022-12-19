# app.theme

Access information about the current theme.

## app.theme.color

```lua
local color = app.theme.color.color_name
```

The [color](color.md) can be used to paint in an
[Image](image.md#image) or a [GraphicsContext](graphicscontext.md#graphicscontext).

List of possible colors:
https://github.com/aseprite/aseprite/blob/3c77928a6f193748bcd8cca15d45000dd58e11d5/data/extensions/aseprite-theme/theme.xml#L33

## app.theme.dimension

```lua
local value = app.theme.dimension.dimension_name
```

Returns a number identified in the dimensions of the theme.
List of possible dimensions:
https://github.com/aseprite/aseprite/blob/3c77928a6f193748bcd8cca15d45000dd58e11d5/data/extensions/aseprite-theme/theme.xml#L11
