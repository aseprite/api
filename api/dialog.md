# Dialog

The dialog class can be used to show input controls/widgets in the
screen to get some data from the user.

Example:

```lua
local dlg = Dialog()
dlg:entry{ id="user_value", label="User Value:", text="Default User" }
dlg:button{ id="confirm", text="Confirm" }
dlg:button{ id="cancel", text="Cancel" }
dlg:show()
local data = dlg.data
if data.confirm then
  app.alert("The given value is '" .. data.user_value .. "'")
end
```

Almost all dialogs functions return the same dialog object so we can
use [method chaining](https://en.wikipedia.org/wiki/Method_chaining).
For example:

```lua
local data =
  Dialog():entry{ id="user_value", label="User Value:", text="Default User" }
          :button{ id="confirm", text="Confirm" }
          :button{ id="cancel", text="Cancel" }
          :show().data
if data.confirm then
  app.alert("The given value is '" .. data.user_value .. "'")
end
```

## Dialog()

```lua
local dlg = Dialog()
local dlg = Dialog(string)
local dlg = Dialog{ title=string,
                    onclose=function }
```

Creates a new dialog. The dialog is hidden, so you have to call
[Dialog:show](#dialogshow) function to make it visible. The
constructor that receives a `string` will use that string in the title
bar of the dialog. The constructor that receives a table can receive a
special callback function (`onclose`) that is called when the dialog
is closed.

## Dialog:button()

```lua
local dlg = Dialog()
dlg:button{ id=string,
            label=string,
            text=string,
            selected=boolean,
            focus=boolean,
            onclick=function }
```

Creates a button.

Arguments (table fields):

* `id`: Identifier for this button. [Dialog.data](#dialogdata) will contain a field
  for each widget with and `id`.
* `label`: Label at the left side of the control.
* `text`: Text of the button.
* `selected`: True in case that you want to show the button checked by default.
* `focus`: Focus this button by default or when the Enter key is pressed in an [text entry](#dialogentry) field.
* `onclick`: Function to be called when the button is pressed.

## Dialog:check()

```lua
local dlg = Dialog()
dlg:check{ id=string,
           label=string,
           text=string,
           selected=boolean,
           onclick=function }
```

Creates a check box. Arguments are the same as in [Dialog:button](#dialogbutton).

## Dialog:close()

```lua
local dlg = Dialog()
dlg:button{ text="Close",
            onclick=function()
                      dlg:close()
                    end }
dlg:show{ wait=false }
```

Closes the dialog from a `onclick` [button](#dialogbutton) event. By
default buttons without an `onclick` event handler will close the
dialog, but if you specify a `onclick` function, you have to call this
function to close the dialog.

## Dialog:color()

```lua
local dlg = Dialog()
dlg:color{ id=string,
           label=string,
           color=app.Color }
```

Creates a button to select a [color](color.md#color).

## Dialog:combobox()

```lua
local dlg = Dialog()
dlg:combobox{ id=string,
              label=string,
              option=string,
              options={ string1,string2,string3... },
              onchange=function }
```

Creates a combo box/drop-down list.

## Dialog.data

```lua
local dlg = Dialog()
local data = dlg.data
dlg.data = data
```

Gets/sets a table with one field for each widget with a given `id`.
For each different kind of widget the field is of a different type:

* [button](#dialogbutton)/[check](#dialogcheck)/[radio](#dialogradio):
  The field is a boolean (true or
  false) if the button is selected or was used to close the dialog.
* [entry](#dialogentry)/[label](#dialoglabel): A string of text.
* [slider](#dialogslider): An integer.
* [number](#dialognumber): An intenger or a
  number depending on the number of decimals of the number field.
* [combobox](#dialogcombobox): A string with the
  selected item.
* [color](#dialogcolor): A [Color](color.md#color).
* [shades](#dialogshades): A table with an array of [Color](color.md#color)s when `mode="sort"`

## Dialog.bounds

```lua
local dlg = Dialog()
local bounds = dlg.bounds
dlg.bounds = Rectangle(x, y, bounds.width, bounds.height)
```

Gets or sets the position and size (a [rectangle](rectangle.md#rectangle)) of
the dialog. This might be useful to align several dialog that must be
shown in the same *xy*-position.

## Dialog:entry()

```lua
local dlg = Dialog()
dlg:entry{ id=string,
           label=string,
           text=string,
           focus=boolean }
```

Creates a text entry.

## Dialog:label()

```lua
local dlg = Dialog()
dlg:label{ id=string,
           label=string,
           text=string }
```

* `id`: Identifier for this label. If you specify it, a field in
  [Dialog.data](#dialogdata) will be created with the given string in
  `text`.
* `label`: Text to be used in the left side.
* `text`: Text to be used in the right side.

Creates a static label.

## Dialog:modify()

```lua
local dlg = Dialog()
dlg:modify{ id=string,
            visible=boolean,
            enabled=boolean,
            text=string }
```

Changes properties of the given widget that matches the identifier `id`.

## Dialog:newrow()

```lua
local dlg = Dialog()
dlg:newrow()
dlg:newrow{ always=true }
```

Indicates that the next widget should be put in a new row in the
dialog (useful to create buttons or several controls of the same type
one below the other).

Using the `newrow{ always=true }` is a way to avoid joining widgets of the
same type (it's like calling `newrow()` after each new widget is added).

## Dialog:number()

```lua
local dlg = Dialog()
dlg:number{ id=string,
            label=string,
            text=string,
            decimals=integer }
```

Creates an entry field to input a number.

## Dialog:radio()

```lua
local dlg = Dialog()
dlg:radio{ id=string,
           label=string,
           text=string,
           selected=boolean,
           onclick=function }
```

Creates a radio button. Arguments are the same as in [Dialog:button](#dialogbutton).

## Dialog:separator()

```lua
local dlg = Dialog()
dlg:separator{ id=string,
               label=string,
               text=string }
```

## Dialog:shades()

```lua
local dlg = Dialog()
dlg:shades{ id=string,
            label=string,
            mode="pick" | "sort",
            colors={ color1, color2, color3, ... },
            onclick=function }
```

Creates a widget with a set of colors that can be clicked/picked (when
`mode="pick"`, which is the default mode) or can be sorted (when
`mode="sort"`, which is the default mode).

The `onclick` function can receive a `event` parameter which is a
table with one `event.color` field which is the color that was
clicked, and a `event.button` field with the
[mouse button](mousebutton.md#mousebutton), for example:

```lua
dlg:shades{
  ...
  onclick=function(ev)
    if ev.button == MouseButton.LEFT then
      -- In this case we change the active foreground color
      -- with the clicked color in the shades widget when
      -- the left mouse button is pressed.
      app.fgColor = ev.color
    elseif ev.button == MouseButton.RIGHT then
      app.bgColor = ev.color
    end
  end
}
```

## Dialog:show()

```lua
local dlg = Dialog()
dlg:show()
dlg:show{
  wait=false,
  bounds=Rectangle()
}
```

Makes the dialog visible to the user. The script code will continue
when the dialog is closed by default (pressing a
[button](#dialogbutton)).

If `{ wait=false }` is used as argument, the dialog is open "in
background", which means that the script code continues the execution
with its following line, and the dialog will be visible until it's
closed with some button or calling [Dialog:close](#dialogclose) in a
`onclick` event.

With `{ bounds=Rectangle() }` you can display the dialog in a specific
location. Useful to show the dialog in a previous position that you
obtain from [Dialog.bounds](#dialogbounds) property.

## Dialog:slider()

```lua
local dlg = Dialog()
dlg:slider{ id=string,
            label=string,
            min=integer,
            max=integer,
            value=integer,
            onchange=function,
            onrelease=function }
```

Creates a slider in the dialog.

## Dialog:file()

```lua
local dlg = Dialog()
dlg:file{ id=string,
          label=string,
          title=string,
          open=boolean,
          save=boolean,
          filename=string | { string1,string2,string3... },
          filetypes={ string1,string2,string3... },
          onchange=function }
```

Creates a text entry field + a button to select one file to open or save, possibilities:

* `open=true`: shows a dialog to open an existent file (this is the default mode).
* `save=true`: shows a dialog to select an existent file to overwrite or a new file to save.

Arguments (table fields):

* `load`: True if you want to show a dialog to the user to select an existent file to load/read.
* `save`: True if you want to show a dialog to the user to select a new file to save/write content.
* `filename`: String of the selected filename to open or save.
* `filetypes`: Array of possible file types/extensions that the user can select.
* `entry`: Show an entry field to edit the filename manually (false by default).
* `focus`: Focus this field by default.
* `onchange`: Function to be called when the filename is changed.
