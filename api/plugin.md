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
        { "path": "./my-script.lua" }
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
    group="cel_popup_properties",
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
extension just double-clicking it should be enough on Windows or
macOS. In other case you can install it from *Edit > Preferences >
Extensions > Add Extension*.

## Plugin.name

Name of the extension.

## Plugin.path

Path where the extension is installed.

## Plugin.preferences

It's a Lua table where you can load/save any kind of Lua value here
and they will be saved/restored automatically on each session.

## Plugin:newCommand()

```lua
function init(plugin)
  plugin:newCommand{
    id="CommandName",
    title="User Friendly Command Name",
    group=string,
    onclick=function()
      ...
    end,
    onenabled=function()
      ...
      return true | false
    end
  }
end
```

Creates a new command that can be associated to keyboard shortcuts and
it's added in the app menu in the specific `"group"`. Groups are defined
in the [`gui.xml` file](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
inside the `<menus>` element.

* `onclick`: Function to be called when the command is executed
  (clicked or an associated keyboard shortcut pressed).
* `onenabled`: Optional function to know if the command should be
  available (enabled or disabled). It should return true if the
  command can be executed right now. If this function is not specified
  the command will be always available to be executed by the user.

## Plugin:newMenuGroup()

```lua
function init(plugin)
  plugin:newMenuGroup{
    id="new_group_id",
    title="Menu Item Label",
    group="parent_group_id"
  }
end
```

Creates a new menu item which will contain a submenu grouping several
plugin commands.

* `id`: ID to identify this new menu group in
  [`Plugin:newCommand{ ..., group=id, ... }`](#pluginnewcommand)
  calls to add several command/menu items as elements of this
  group submenu.
* `group`: In which existent group we should add this new menu item.
  Existent app groups are defined in the
  [`gui.xml` file](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
  inside the `<menus>` element.

## Plugin:newMenuSeparator()

```lua
function init(plugin)
  plugin:newMenuSeparator{
    group="group_id"
  }
end
```

Creates a menu separator in the given menu group, useful to separate
several [Plugin:newCommand](#pluginnewcommand).
