# Editor

References a sprite editor. At the moment we can access only the
active editor using [app.editor](app.md#appeditor).

## Editor.sprite

```lua
local sprite = app.editor.sprite
```

Returns the [sprite](sprite.md#sprite) in the editor.

## Editor.spritePos

```lua
local point = app.editor.spritePos
```

Returns a [point](point.md#point) of the the mouse position on the
sprite, i.e. what pixel is going to be changed if the user clicks the
mouse.

## Editor.mousePos

```lua
local point = app.editor.mousePos
```

Returns a [point](point.md#point) indicating the mouse position on the
screen.

## Editor:askPoint()

```lua
app.editor:askPoint{
  title=string,
  point=initialPoint,
  onclick=function(ev) ... end,
  onchange=function(ev) ... end,
  oncancel=function(ev) ... end,
}
```

Asks the user to select a pixel/point on the sprite. It's similar to
what happens when you choose *Edit > New Brush* (but in that case you
select a rectangle).

* `title`: Text to show in the [context bar](https://www.aseprite.org/docs/context-bar/)
* `point`: Initial point to highlight (optional)
* `onclick`: Happens when the user clicks (press/release a mouse button) on the canvas
* `onchange`: Happens when the user drags the mouse (press/move mouse/release a mouse button) on the canvas
* `oncancel`: Happens when the user cancels the action (e.g. press the <kbd>Escape</kbd> key)

## Editor:cancel()

```lua
app.editor:cancel()
```

Cancels the [editor:askPoint()](#editoraskpoint) action.
