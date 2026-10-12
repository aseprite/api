# Plugin

Since Aseprite v1.2.18 [plugins](https://www.aseprite.org/docs/extensions/) (also called extensions) can be created with scripts. 

When making a script plugin, two different things are required: a [`package.json`](#packagejson) file and a [`.lua` script file](#script-file). The files then need to be compressed into a `.zip` file, with the `.zip` extension renamed to [`.aseprite-extension`](https://www.aseprite.org/docs/extensions/#file-content). This will create an Aseprite plugin file.

The plugin can then be installed by double-clicking the file. Alternatively, it can be installed from [*Edit > Preferences > Extensions > Add Extension*](https://www.aseprite.org/docs/extensions#add/remove-extensions).

### package.json

The `package.json` is a `.json` file that contains basic metadata for the plugin, like its name, author, and scripts.

Example:
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

Multiple scripts can be defined:

```json
  "contributes": {
    "scripts": [
        { "path": "./my-script.lua" },
        { "path": "./my-other-script.lua" },
        { "path": "./my-library-script.lua" }
    ]
  }
```

### Script file

A plugin file needs to contain at least one `.lua` script file. The relative file path needs to be in the `scripts` property of the `package.json` for Aseprite to run the script. 

To access the `Plugin` object, the `init` global function, which is called when the plugin is initialized, must be defined in the script file. It has one parameter: the plugin's Plugin object. Multiple `.lua` files can define the `init` function.

```lua
function init(plugin)
  print("Aseprite is initializing "..plugin.displayName)
end
```

Similarly, an `exit` function can be defined, which is called upon the plugin closing. The `exit` function also has the plugin's Plugin object as a parameter.

```lua
function exit(plugin)
  print("Aseprite is closing my plugin :(")
end
```

A complete example:

```lua
function init(plugin)
  print("Aseprite is initializing my plugin")

  -- We can use "plugin.preferences" as a table with fields for
  -- our plugin (these fields are saved between sessions)
  if plugin.preferences.count == nil then
    plugin.preferences.count = 0
  end

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

## Plugin.name

Name of the extension. Corresponds with the `name` property in the plugin's `package.json` file.

## Plugin.displayName

Display name of the extension. Corresponds with the `displayName` property in the plugin's `package.json` file.

## Plugin.version

Version of the extension. Corresponds with the `version` property in the plugin's `package.json` file.

## Plugin.path

Absolute path where the extension is installed.

## Plugin.preferences

A table in which any kind of value can be loaded/saved and will be saved/restored automatically on each session. This is useful for storing things like settings and other things that need to persist after the Plugin has been relaunched.

## Plugin:newCommand()

```lua
function init(plugin)
  plugin:newCommand{
    id="CommandID",
    title="User Friendly Command Name",
    group=string,
    onclick=function()
      ...
    end,
    onenabled=function()
      ...
      return true or false
    end,
    onchecked=function()
      ...
      return true or false
    end
  }
end
```

Creates a new [command](app_command.md#appcommand) that can be associated with keyboard shortcuts and
can be added to a `group` in a menu.

* `id`: The id of the command. The command can be called with app.command.`id`() (e.g: `app.command.CommandName()`).
* `title`: The title of the command. This will be what the user sees in a menu or in the [Run Command](https://www.aseprite.org/docs/run-command#run-command) window.
* `group`: Optional parameter that specifies a menu group for the command to be added to. Groups are defined in the [`gui.xml` file](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
inside the `<menus>` element.
* `onclick`: Function to be called when the command is executed
  (clicked in a menu or an associated keyboard shortcut pressed).
* `onenabled`: Optional function to check if the command should be enabled. It should return true if the command can be executed, and return false if it cannot. If this function is not specified, the command will always be available to be executed by the user. This function is called every time the command is displayed in a menu (e.g., when a dropdown is opened), as well as 
* `onchecked`: Optional function to check whether the command should have a checkbox. This is called every time the command is displayed in a menu (e.g., when a dropdown is opened). It should return true if the command should have a checked checkbox next to it.

## Plugin:deleteCommand()

```lua
function init(plugin)
  plugin:deleteCommand("CommandID")
  plugin:deleteCommand{
    id="CommandID",
  }
end
```

Deletes the given [command](app_command.md#appcommand)'s functionality. Accepts a string, which is the command's `id`. The command's name and menu item will still exist, but clicking on or running the command will not do anything. Built-in commands can be deleted.

## Plugin:newMenuGroup()

```lua
function init(plugin)
  plugin:newMenuGroup{
    id="group_id",
    title="Menu Item Label",
    group="parent_group_id"
  }
end
```

Creates a new menu item which will contain a submenu grouping several
plugin commands.

* `id`: ID to identify this new menu group in
  [`Plugin:newCommand{ ..., group=id, ... }`](#pluginnewcommand)
  calls to add several commands/menu items as elements of this
  group submenu.
* `title`: The title/label of the group.
* `group`: Specifies the existing group to which this new menu item should be added.
  Existing app groups are defined in the
  [`gui.xml` file](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
  inside the `<menus>` element.

## Plugin:deleteMenuGroup()

```lua
function init(plugin)
  plugin:deleteMenuGroup("group_id")
  plugin:deleteMenuGroup{
    id="group_id",
  }
end
```

Deletes the specified menu group. Accepts a string, which is the group's `id`. Unlike [Plugin:deleteCommand()](#plugindeletecommand), the group is visually removed from its menu. The group's contained commands are not deleted and can still be run, they just will not be visible in the menu (because the group was deleted); they are also still visible in the [Run Command](https://www.aseprite.org/docs/run-command#run-command) window. Built-in menu groups cannot be deleted.

## Plugin:newMenuSeparator()

```lua
function init(plugin)
  plugin:newMenuSeparator{
    group="group_id"
  }
end
```

Creates a menu separator in the given menu `group`, useful to separate
several [Plugin:newCommand](#pluginnewcommand) calls.

## Plugin:newFileFormat()

```lua
function init(plugin)
  plugin:newFileFormat{
    name=string,
    binary=boolean,
    supports=FormatSupport,
    extensions={ string },
    onload=function(ev) end,
    onsave=function(ev) end
  }
end
```

Registers a new file format handler. This allows custom file formats to be used with Aseprite.

* `name`: Optional, will use the first extension registered otherwise
* `binary`: Optional, whether the file will be opened in binary mode or not (set to `false` for text-only formats, otherwise defaults to `true`)
* `supports`: Optional, a set of flags specifying the capabilities of this format, see [FormatSupport](formatsupport.md) for a description of each flag. Defaults to `FormatSupport.RGB | FormatSupport.RGBA | FormatSupport.GRAY | FormatSupport.GRAYA | FormatSupport.INDEXED`.
* `extensions`: The extension to be registered, without the dot ("."). They cannot overlap with an existing format that Aseprite supports (for example, "png"), if the format has already been registered by either Aseprite itself or another plugin, registration will fail with an error.
* `onload/onsave`: The function that is called for the extension to convert the given file to one or multiple Sprites. It is called with a table argument containing a `file` and `filename`. The `file` is an open Lua file handle to whatever we're loading or saving. For loading, this function must return a Sprite object on success, or raise an error otherwise. For saving, the function should return a boolean on success or failure, or raise an error to give the user more details.

For an example of a minimal implementation of a file format, see [aseprite-ppm-example](https://github.com/ckaiser/aseprite-ppm-example).

