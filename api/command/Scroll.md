# Scroll

```lua
app.command.Scroll {
  direction=string,
  units=string,
  quantity=int
}
```

Scrolls the active editor view according to the given parameters.

* `direction`: The selection will be moved to a specific direction, can be `"left"`, `"right"`, `"up"` or `"down"`.
`units`: The unit to use for `quantity`. Can be `"pixel"`, `"tile-width"`, `"tile-height"` `"zoomed-pixel"`, `"zoomed-tile-width"`, `"zoomed-tile-height"`, `"viewport-width"`, `"viewport-height"`.
* `quantity`: the number of `pixel`s, or `tile-width`s, etc. to move the selection to the given `direction` depending on the `units`.

# Example

```lua
app.command.Scroll{
    quantity=50,
    units="pixel",
    direction="right"
}
```