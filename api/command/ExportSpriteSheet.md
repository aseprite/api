# ExportSpriteSheet

```lua
app.command.ExportSpriteSheet {
  ui=true,
  recent=true,
  askOverwrite=true,
  type=SpriteSheetType.HORIZONTAL,
  columns=0,
  rows=0,
  width=0,
  height=0,
  bestFit=false,
  textureFilename="",
  dataFilename="",
  dataFormat=SpriteSheetDataFormat.JSON_HASH,
  filenameFormat="{title} ({layer}) {frame}.{extension}",
  borderPadding=0,
  shapePadding=0,
  innerPadding=0,
  trimSprite=false,
  trim=false,
  trimByGrid=false,
  extrude=false,
  ignoreEmpty=false,
  mergeDuplicates=false,
  openGenerated=false,
  layer="",
  tag="",
  splitLayers=false,
  splitTags=false,
  splitGrid=false,
  listLayers=true,
  listTags=true,
  listSlices=true,
  fromTilesets=false,
}
```

This is similar to
using [the `-sheet` argument from the CLI](https://www.aseprite.org/docs/cli/#sheet).

* `ui`: Shows the dialog to export the sprite sheet.
* `recent`: Only available since v1.3.7, it adds the output file
  (`textureFilename`) to the list of recent files. By default, if it's
  not specified, it depends on the `ui` parameter: if the Export
  Sprite Sheet dialog is displayed, the selected output filename will
  be added to the recent list.
* `askOverwrite`
* `type` ([SpriteSheetType](../spritesheettype.md#spritesheettype))
* `columns`
* `rows`
* `width`
* `height`
* `bestFit=false`
* `textureFilename`
* `dataFilename`
* `dataFormat` ([SpriteSheetDataFormat](../spritesheetdataformat.md#spritesheetdataformat))
* `filenameFormat`
* `borderPadding`
* `shapePadding`
* `innerPadding`
* `trimSprite`
* `trim`
* `trimByGrid`
* `extrude`
* `ignoreEmpty`
* `mergeDuplicates`
* `openGenerated`
* `layer`
* `tag`
* `splitLayers`
* `splitTags`
* `splitGrid`: Only available since v1.3-beta21
* `listLayers`
* `listTags`
* `listSlices`
* `fromTilesets`: Only available since v1.3-beta21, export tileset,
  like [ExportTileset](ExportTileset.md#exporttileset)
