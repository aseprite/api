# MouseEvent

This object is received as first parameter in the function associated
to `onmousedown`, `onmouseup`, `onmousemove`, or `onwheel` events of a
[canvas](dialog.md#dialogcanvas) widget.

## MouseEvent.x

```lua
  onmousedown=function(ev)
    print('mouse button pressed in', ev.x, ev.y)
  end
```

The (x,y) position of the mouse when the event happens, in client
coordinates, where (0,0) is the top-left corner of the canvas widget.

## MouseEvent.y

See [MouseEvent.x](#mouseeventx)

## MouseEvent.button

The [MouseButton](mousebutton.md#mousebutton) pressed or released by
the user.

## MouseEvent.pressure

The pressure of pen when the event is generated from a stylus.

## MouseEvent.deltaX

Only for the `onwheel` event.

## MouseEvent.deltaY

Only for the `onwheel` event.

## MouseEvent.altKey

True if the <kbd>Alt</kbd> key was pressed when the event occurs.

## MouseEvent.metaKey

True if the <kbd>Windows</kbd> key (or <kbd>Command</kbd> key on
macOS) was pressed when the event occurs.

## MouseEvent.ctrlKey

True if the <kbd>Ctrl</kbd> key was pressed when the event occurs.

## MouseEvent.shiftKey

True if the <kbd>Shift</kbd> key was pressed when the event occurs.

## MouseEvent.spaceKey

True if the <kbd>Space</kbd> key was pressed when the event occurs.
