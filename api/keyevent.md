# KeyEvent

This object is received as first parameter in the function associated
to `onkeydown` or `onkeyup` events of a
[canvas](dialog.md#dialogcanvas) widget.

## KeyEvent.repeatCount

Number of times the key was autorepeated. This can happen when the
user presses and holds a key.

## KeyEvent.key

A string containing the pressed/released Unicode character.

## KeyEvent.code

A string that identifies the pressed/released key, similar to the values found
in https://developer.mozilla.org/en-US/docs/Web/API/UI_Events/Keyboard_event_code_values,
one of the following values:

```lua
  "Unidentified"
  "KeyA"
  "KeyB"
  "KeyC"
  "KeyD"
  "KeyE"
  "KeyF"
  "KeyG"
  "KeyH"
  "KeyI"
  "KeyJ"
  "KeyK"
  "KeyL"
  "KeyM"
  "KeyN"
  "KeyO"
  "KeyP"
  "KeyQ"
  "KeyR"
  "KeyS"
  "KeyT"
  "KeyU"
  "KeyV"
  "KeyW"
  "KeyX"
  "KeyY"
  "KeyZ"
  "Digit0"
  "Digit1"
  "Digit2"
  "Digit3"
  "Digit4"
  "Digit5"
  "Digit6"
  "Digit7"
  "Digit8"
  "Digit9"
  "Numpad0"
  "Numpad1"
  "Numpad2"
  "Numpad3"
  "Numpad4"
  "Numpad5"
  "Numpad6"
  "Numpad7"
  "Numpad8"
  "Numpad9"
  "F1"
  "F2"
  "F3"
  "F4"
  "F5"
  "F6"
  "F7"
  "F8"
  "F9"
  "F10"
  "F11"
  "F12"
  "Escape"
  "Backquote"
  "Minus"
  "Equal"
  "Backspace"
  "Tab"
  "BracketLeft"
  "BracketRight"
  "Enter"
  "Semicolon"
  "Quote"
  "Backslash"
  "Comma"
  "Period"
  "Slash"
  "Space"
  "Insert"
  "Delete"
  "Home"
  "End"
  "PageUp"
  "PageDown"
  "ArrowLeft"
  "ArrowRight"
  "ArrowUp"
  "ArrowDown"
  "NumpadDivide"
  "NumpadMultiply"
  "NumpadSubtract"
  "NumpadAdd"
  "NumpadComma"
  "NumpadEnter"
  "PrintScreen"
  "Pause"
  "IntlYen"
  "KanaMode"
  "Convert"
  "NonConvert"
  "NumpadEqual"
  "Backquote"
  "ShiftLeft"
  "ShiftRight"
  "ControlLeft"
  "ControlRight"
  "AltLeft"
  "AltRight"
  "MetaLeft"
  "MetaRight"
  "ContextMenu"
  "MetaLeft"
  "ScrollLock"
  "NumLock"
  "CapsLock"
```

## KeyEvent.altKey

True if the <kbd>Alt</kbd> key was pressed when the event occurs.

## KeyEvent.metaKey

True if the <kbd>Windows</kbd> key (or <kbd>Command</kbd> key on
macOS) was pressed when the event occurs.

## KeyEvent.ctrlKey

True if the <kbd>Ctrl</kbd> key was pressed when the event occurs.

## KeyEvent.shiftKey

True if the <kbd>Shift</kbd> key was pressed when the event occurs.

## KeyEvent.spaceKey

True if the <kbd>Space</kbd> key was pressed when the event occurs.

## KeyEvent:stopPropagation()

Stops propagating this event to other parent widget/main Aseprite
window. Use this in case that your canvas widget used the key and you
want to avoid triggering a command with a keyboard shortcut.
