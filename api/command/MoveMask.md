# MoveMask

```lua
app.command.MoveMask {
  target=string,
  wrap=bool,
  direction=string,
  units=string,
  quantity=int
}
```

Moves the selection boundaries or its content (pixels).

* `target` (string): must be
  * `'boundaries'` to modify selection boundaries only or
  * `'content'` to modify the selection content ([active cel](../app.md#appcel) pixels)
* `wrap`: `true` or `false`, when true it does the *Edit > Shift* effect,
  were pixels from one side in will appear from the other side (so the
  content is shifted and pixels wrapped, so the selection boundaries
  is not moved at all, only pixels inside it)
* `direction`: The selection will be moved to a specific direction, can be `"left"`, `"right"`, `"up"` or `"down"`.
`units`: The unit to use for `quantity`. Can be `"pixel"`, `"tile-width"`, `"tile-height"` `"zoomed-pixel"`, `"zoomed-tile-width"`, `"zoomed-tile-height"`, `"viewport-width"`, `"viewport-height"`.
* `quantity`: the number of `pixel`s, or `tile-width`s, etc. to move the selection to the given `direction` depending on the `units`.
