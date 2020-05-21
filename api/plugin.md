# Plugin

Since Aseprite v1.2.18 we can create
[plugins](https://www.aseprite.org/docs/extensions/) with scripts.

To create a plugin we have to create a folder with a `package.json` file. For example:

```json
{
  "name": "my-scripts",
  "displayName": "My Scripts",
  "description": "My scripts do something",
  "version": "0.1",
  "author": { "name": "FirstName LastName",
              "email": "my@email.com",
              "url": "https://mywebsite.com/" },
  "contributors": [ ],
  "publisher": "myname",
  "license": "CC-BY-4.0",
  "categories": [ "Scripts" ],
  "contributes": {
    "scripts": [
        { "path": "./my-script.lua" },
    ]
  }
}
```

Then we create a `my-script.lua` file inside the folder. For example:

```lua
function init(plugin)
  print("Aseprite is initializing my plugin")

  -- we can use "plugin.preferences" as a table with fields for
  -- our plugin (these fields are saved between sessions)
  if plugin.preferences.count == nil then
    plugin.preferences.count = 0
  end

  --
  plugin:newCommand{
    id="MyFirstCommand",
    title="My First Command",
    group="cel_popup",
    onclick=function()
      plugin.preferences.count = plugin.preferences.count+1
    end
  }
end

function exit(plugin)
  print("Aseprite is closing my plugin, MyFirstCommand was called "
        .. plugin.preferences.count .. " times")
end
```

Then we compress both files (`package.json` and `my-script.lua`) in a
`.zip`, and rename the `.zip` to `.aseprite-extension`. To install the
extension just double-clicking just be enough on Windows or macOS.

## Plugin.preferences

## Plugin:newCommand
