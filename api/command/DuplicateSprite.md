# DuplicateSprite

```lua
app.command.DuplicateSprite {
  ui=bool,
  filename=string,
  flatten=bool
}
```

Duplicates the current sprite

* `ui`: Shows the duplicate dialog, `true` by default. Set to `false` to create the duplicate automatically.
* `filename`: New filename for the sprite, if left empty it will auto-generate a new one.
* `flatten`: Duplicate merged layers only. Defaults to `false`.
