# Tool

References a drawing tool. At the moment this class is used only to
get and set the active tool
([`app.tool`](app.md#apptool)), or to paint on the canvas
(`tool` parameter in [`app.useTool()`](app.md#appusetool)).

If a function receives a tool, it can receive a tool ID too.

## Tool.id

```lua
local id = app.tool.id
```

Returns the identifier (a string) of the specified in the
[`gui.xml`](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
file ([example](https://github.com/aseprite/aseprite/blob/20618ff321ae4e73a4f5d6bfd9ef6f2cd8925b7a/data/gui.xml#L1065)).
