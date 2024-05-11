# SaveFile

```lua
app.command.SaveFile {
  ui=true,
  recent=true,
  filename="",
  filenameFormat="",
  tag="",
  aniDir=AniDir,
  slice="",
  fromFrame=frame,
  toFrame=frame,
  ignoreEmpty=false,
  bounds=Rectangle,
}
app.command.SaveFileAs { ... }
app.command.SaveFileCopyAs { ... }
```

Saves the current image in a specific file. These 3 commands have
little differences by default:

* `SaveFile`: It's like *File > Save* option. It will try to save the
  active sprite with its already associated file, in other case acts
  like the `SaveFileAs` showing the dialog to select the filename.
* `SaveFileAs`: It's like *File > Save As* option. Saves the active
  sprite in a new file (shows the dialog to select a file by default).
  The active sprite filename will be changed to the new selected filename.
* `SaveFileCopyAs`: It's like *File > Export* option. Saves a copy of
  the active sprite in other file. The filename will be kept intact.

Parameters:

* `ui`: Shows the dialog to select the filename. `SaveFile` doesn't
  show the UI (`false` by default) if the sprite has an associated
  file.  `SaveFileAs` and `SaveFileCopyAs` will show the UI by
  default.
* `recent`: Only available since v1.3.7, it adds the file to the list
  of recent files. By default it depends if the dialog to select the
  filename is displayed (depends on the value of the `ui` parameter).
* `filename`: The filename where to save the sprite. The default
  values is the
* `filenameFormat`: Special value similar to [--filename-format](https://www.aseprite.org/docs/cli/#filename-format)
  when we use [--save-as](https://www.aseprite.org/docs/cli/#save-as) from the [CLI](https://www.aseprite.org/docs/cli/)
* `tag`: A tag name. You can save only the range of frames specified by this tag.
* `aniDir`: By default it is
  [AniDir.FORWARD](../anidir.md#anidirforward), but you can specify
  any [AniDir](../anidir.md#anidir)
* `slice`: A slice name (to save only a specific portion of the sprite)
* `fromFrame`/`toFrame`: A range of [frames](../frame.md#frame) to save.
* `ignoreEmpty`: `false` by default, but it can be `true` in case that
  you want to avoid saving empty frames of a sequence of files
  (e.g. when saving an animation as `frame01.png`, `frame02.png`,
  etc.).
* `bounds`: Available since v1.3-beta21: Only export the selected
  [rectangle](../rectangle.md#rectangle) of the canvas.
