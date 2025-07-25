# ColorQuantization

```lua
app.command.ColorQuantization {
  ui=bool,
  withAlpha=bool,
  maxColors=int,
  useRange=bool,
  algorithm=string,
}
```

Creates a palette from the current sprite

* `ui`: Shows the dialog on the screen, `true` by default.
* `withAlpha`: Create entries with alpha component, defaults to `true`
* `maxColors`: Color amount limit, defaults to `256`
* `useRange`: Replace current range, defaults to `false`
* `algorithm`: One of `"default"`, `"rgb5a3"` or `"octree"`

## Example

```lua
app.command.ColorQuantization {
  ui=true,
  withAlpha=false,
  maxColors=100,
  algorithm="octree"
}
```
