# app.preferences

```lua
local value = app.preferences.section.option
app.preferences.section.option = newValue
```

Gets or sets the given preference `option` in the given `section`. You
can find valid `section` and `option` names in the
[pref.xml](https://github.com/aseprite/aseprite/blob/main/data/pref.xml)
file.

## app.preferences.tool()

```lua
local toolPref = app.preferences.tool(tool)
local value = toolPref.section.option
toolPref.section.option = newValue
```

Returns the preferences of the given [`tool`](tool.md#tool).

## app.preferences.document()

```lua
local docPref = app.preferences.document(sprite)
local value = docPref.section.option
docPref.section.option = newValue
```

Returns the preferences of the given [`sprite`](sprite.md#sprite).
