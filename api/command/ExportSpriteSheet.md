# ExportSpriteSheet

```lua
app.command.ExportSpriteSheet {
  ui=true,
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
  borderPadding=0,
  shapePadding=0,
  innerPadding=0,
  trim=false,
  extrude=false,
  openGenerated=false,
  layer="",
  tag="",
  splitLayers=false,
  listLayers=true,
  listTags=true,
  listSlices=true
}
```

This is similar to
using [the `-sheet` argument from the CLI](https://www.aseprite.org/docs/cli/#sheet).

* `ui`
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
* `borderPadding`
* `shapePadding`
* `innerPadding`
* `trim`
* `openGenerated`
* `layer`
* `tag`
* `splitLayers`
* `listLayers`
* `listTags`
* `listSlices`
