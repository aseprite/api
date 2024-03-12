# ExportTileset

```lua
app.command.ExportTileset {
  dataFormat=SpriteSheetDataFormat.JSON_ARRAY,
  fromTilesets=true
}
```

This is similar to
using [the `-export-tileset` argument from the CLI](https://www.aseprite.org/docs/cli/#export-tileset)
with [`-format=json-array` option](https://www.aseprite.org/docs/cli/#format).

This command accept the same parameters as [app.command.SaveFileCopyAs](SaveFile.md#savefile).
