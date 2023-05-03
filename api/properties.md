# Properties

Some objects like a [Sprite](sprite.md#sprite),
[Layer](layer.md#layer), [Cel](cel.md#cel), [Slice](slice.md#slice),
[Tag](tag.md#tag), [Tileset](tileset.md#tileset), [Tile](tile.md#tile),
contains some special fields like `.color` and `.data` to store an
user-defined [color](color.md#color) or an user-defined text (any text).

Anyway, since **Aseprite 1.3-rc1** you can have user-defined and
extension-defined properties for each of these objects. We'll use an
`object` in the following examples, as it can be of any kind (Sprite,
Layer, etc.)

## User-defined properties

```lua
object.properties.myInteger = 1
object.properties.myNumber = 1.2
object.properties.myString = "value"
object.properties.myVector = { 1, 2, 3, ... }
object.properties.myMap = { x=1, y=... }
object.properties = { myInteger=1, myNumber=1.2, ... }
```

You can set one property at a time, or all properties at the same
time. Each time a property is set, it generates undo information.

* The syntax `object.properties = { ... }` sets the user-defined
  properties, but doesn't modify the properties related to extensions

## Extension-defined properties

```lua
local pluginKey = "publisher/extension-name"

object.properties(pluginKey).extInteger = 1
object.properties(pluginKey).extString = "value"
object.properties(pluginKey).extVector = { 1, 2, 3, ... }
object.properties(pluginKey).extMap = { x=1, y=... }
object.properties(pluginKey, { extInteger=1, extString=1.2, ... })
```

Extensions can define their own properties if they need them.  Each
time a property is set, it generates undo information.

Some important points:

* The given `pluginKey` must be equal to `publisher/name`, where
  `name` is the name of the plugin, and `publisher` the name/ID of the
  author of this extension (e.g. GitHub username). These values are
  specified in the `package.json` file of the [plugin](plugin.md#plugin)
* The syntax `object.properties(pluginKey, { ... })` is used to set
  all the properties related to the extension in the given `object`
* Using a `pluginKey=""` is exactly the same as accessing the
  user-defined properties
