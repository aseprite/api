# TouchEvent

This object is received as first parameter in the function associated
to `ontouch` event of a [canvas](dialog.md#dialogcanvas) widget.

## TouchEvent.x

```lua
  ontouch=function(ev)
    print('touch event pressed in', ev.x, ev.y)
  end
```

The (x,y) position of the touch when the event happens, in client
coordinates, where (0,0) is the top-left corner of the canvas widget.

## TouchEvent.y

See [TouchEvent.x](#toucheventx).

## TouchEvent.magnification

Magnification factor to apply.
