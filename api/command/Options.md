# Options

```lua
app.command.Options()
```

Opens the Aseprite preferences dialog.


This command can also be used to prompt the user to install an Aseprite extension file.

## Example

```lua
app.command.Options {
  installExtension="" 
}
```

Parameters:

* `installExtension`: the path to the `*.aseprite-extension` file to be installed
