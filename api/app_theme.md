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

## app.theme:styleMetrics()

```lua
local data = app.theme:styleMetrics(style_id)
local leftBorder = data.border.left
local topBorder = data.border.top
local rightBorder = data.border.right
local bottomBorder = data.border.bottom
```

Returns information about the given style ID (`style_id` must be a
string). The returned information at the moment includes a `border`
field which is a table with `left`/`top`/`right`/`bottom` border
dimension in pixels (they already have
[app.uiScale](app.md#appuiscale) applied).

List of possible styles:
https://github.com/aseprite/aseprite/blob/0c092cc37c193786bad702c0830b739f5ff808e0/data/extensions/aseprite-theme/theme.xml#L446
