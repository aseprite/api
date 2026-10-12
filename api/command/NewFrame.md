# NewFrame

```lua
app.command.NewFrame {
  content=string
}
```

Creates a frame, or duplicates a frame/frame range. 

* `content`: The content of the frame, defaults to `"current"`. One of `"current"`, `"empty"`, `"cel"`, `"celcopies"`, `"cellinked"`:
  * `"current"`: Duplicates the current frame (the same as *Frame > New Frame*). The new frame is inserted after the current frame.
  * `"empty"`: Creates a new empty frame (the same as *Frame > New Empty Frame*). The new empty frame is inserted after the current frame.
  * `"cel"`, `"celcopies"`, `"cellinked"`: Duplicates the [frame range](https://www.aseprite.org/docs/range#selected-range) cel content into the cels of the succeeding frames, overwriting them; if there aren't enough frames to duplicate into, the missing frames will be created. While the three options function similarly, they differ in how [linked cels](https://www.aseprite.org/docs/linked-cels/) are handled:
    * `"celcopies"`: Duplicated cels are *never* linked with their originals, even if the layer is [continuous](https://www.aseprite.org/docs/continuous-layers#continuous-layers) (the same as *Frame > Duplicate Cels*).
    * `"cellinked"`: Duplicated cels are *always* linked with their originals, even if the layer is discontinuous (the same as *Frame > Duplicate Linked Cels*).
    * `"cel"`: A hybrid of `"celcopies"` and `"cellinked"`; duplicate cels in continuous layers will link with their originals, and duplicate cels in discontinuous layers will not (the same as the *Duplicate Cels w/Layer Mode* command).
