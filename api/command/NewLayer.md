# NewLayer

```lua
app.command.NewLayer {
  name="",
  group=false,
  reference=false,
  ask=false,
  fromFile=false,
  fromClipboard=false,
  viaCut=false,
  viaCopy=false,
  top=false,
  before=false
}
```

* name (string)
  * The name of the layer
* group (boolean)
  * If true, make the new layer a group layer; this option is mutually exclusive to `reference`
* reference (boolean)
  * If true, make the new layer a reference layer; this option is mutually exclusive to `group`
* ask (boolean)
  * `true` or `false`, when true ask the user for a name if inside the interface
* fromFile (boolean)
  * `true` or `false`, when true the layer is created from a file
* fromClipboard (boolean)
  * `true` or `false`, when true the layer takes on the image data from the clipboard
* viaCut (boolean)
  * `true` or `false`, when true the selected image data is cut and moved into the new layer
* viaCopy (boolean)
  * `true` or `false`, when true the selected image data is copied into the new layer
* top (boolean)
  * `true` or `false`, when true the newly created layer is placed at the top of the list
* before (boolean)
  * `true` or `false`, when true the newly created layer is placed before the currently active layer; but if false it is placed after
