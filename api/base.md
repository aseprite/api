# Base library

## require()

```lua
local library = require "library"
```

Returns a pointer to the given library/module. This function will try
to find the `library.lua` file in the same folder of the script that
was executed, or if it's running a [plugin](plugin.md#plugin), it will
try to find `library.lua` from the plugin folder.

Libraries between plugins are not shared, as they will be stored in
the `_LOADED` table with the [plugin.name](plugin.md#pluginname) as a
prefix (e.g. `plugin-name/module`) to avoid conflicts between similar
library names.

More details in the Programming in Lua book: https://www.lua.org/pil/8.1.html

## assert()

```lua
assert(condition)
```

Prints an error message when `condition` is `false` and stops the
execution of the script. This method is used for unit-testing.

## print()

```lua
print(object)
print(object1, object2, ...)
```

Prints the given objects (generally strings) into the console (the
Terminal if we're executing the script in `--batch` or `--shell`
mode).
