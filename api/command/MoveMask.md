# MoveMask

Moves the selection boundaries or its content (pixels).

```lua
app.command.MoveMask {
  target='boundaries' | 'content',
  wrap=false,
  direction='left' | 'right' | 'up' | 'down',
  units='pixel',
  quantity=1
}
```

* `target` (string): must be
  * `'boundaries'` to modify selection boundaries onlyor
  * `'content'` to modify the selection content ([active cel](../app.md#appcel) pixels)
* `wrap`: `true` or `false`, when true it does the *Edit > Shift* effect,
  were pixels from one side in will appear from the other side (so the
  content is shifted and pixels wrapped, so the selection boundaries
  is not moved at all, only pixels inside it)
* `direction` (string): the selection will be moved to a specific direction:
  * `'left'`
  * `'right'`
  * `'up'`
  * `'down'`
* `units` (string): must be one of these options (generally `pixel` is
  enough for scripts, and other options are just for UI):
  * `'pixel'`
  * `'tile-width'`
  * `'tile-height'`
  * `'zoomed-pixel'`
  * `'zoomed-tile-width'`
  * `'zoomed-tile-height'`
  * `'viewport-width'`
  * `'viewport-height'`
* `quantity`: the number of `pixel`s, or `tile-width`s, etc. to move
  the selection to the given `direction` depending on the `units`
