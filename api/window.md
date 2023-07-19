# Window

References a window of the program. At the moment we can access only
the main window using [app.window](app.md#appwindow).

## Window.width

```lua
local width = app.window.width
```

Returns the width of the main window.

## Window.height

```lua
local height = app.window.height
```

Returns the height of the main window.

## Window.events

Returns the [`Events`](events.md#events) object to associate functions
that can act like listeners of specific `Window` events. E.g.

```lua
app.window.events:on('resize',
  function(ev)
    print('Now the main window is', ev.width, ev.height)
  end)
```

Available events for a `Window`:

* `'resize'`: When the user resizes the window.
