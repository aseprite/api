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

Each time we add a new widget like `:button{ ... }` some common properties
can be specified for every kind of widget:

```lua
Dialog:widget_type{
  id=string,
  label=string,
  focus=boolean,
  enabled=boolean,
  visible=boolean,
  hexpand=boolean,
  vexpand=boolean,
}
```

Where:
* `id`: It's the ID to identify this widget in [Dialog.data](#dialogdata)
* `label`: Label at the left side of the widget
* `focus`: Focus this widget by default (useful to focus a specific
  [entry](#dialogentry) when the dialog appears on the screen for the
  first time)
* `enabled`: Enable or disable the widget by default
* `visible`: Make the widget visible or hidden by default
* `hexpand`: Expand the widget horizontally (useful to make a [canvas](#dialogcanvas) with fixed size if we specify `hexpand=false`)
* `vexpand`: Expand the widget vertically (useful to make a [canvas](#dialogcanvas) with fixed size if we specify `vexpand=false`)

## Dialog()

```lua
local dlg = Dialog()
local dlg = Dialog(string)
local dlg = Dialog{ title=string,
                    notitlebar=false,
                    parent=otherDialog,
                    onclose=function }
```

Creates a new dialog. The dialog is hidden, so you have to call
[Dialog:show](#dialogshow) function to make it visible. The
constructor that receives a `string` will use that string in the title
bar of the dialog. The constructor that receives a table can receive a
special callback function (`onclose`) that is called when the dialog
is closed.

The `{ parent=otherDialog }` can be used to display an alert/subdialog
inside a parent dialog (the parent dialog is blocked until the
child dialog is closed).

The `{ notitlebar=true }` can be used to display a dialog without any
kind of title bar (the dialog must be closed with a button inside it).

Returns `nil` if there is no UI available, i.e. [app.isUIAvailable is `false`](app.md#appisuiavailable).

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
           color=app.Color,
           onchange=function }
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

* `options`: Indicates a list of available options in the combobox.
* `option`: Indicates the default selected option in the combobox (one of the `options`).

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
           focus=boolean,
           onchange=function }
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

```lua
local dlg = Dialog()
dlg:modify{ title = "New Dialog Title" }
```

Using the `dialog:modify` with a parameter `title` changes the dialog title.

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
            decimals=integer,
            onchange=function }
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
  bounds=Rectangle(),
  autoscrollbars=false,
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

Setting `{ autoscrollbars=true }` will add scrollbars automatically only
if they are needed. This means that if your dialog contains enough widgets
to make it go out of the window/screen (depending if you are using single
window UI or multiple windows UI) then scrollbars will be shown into your
dialog when its content doesn't fit its bounds.

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

## Dialog:tab()

```lua
local dlg = Dialog()
dlg:tab{ id=string,
         text=string,
         onclick=function }
```

If called for the first time (or anytime after a
[Dialog:endtabs](#dialogendtabs) call), it creates a new tabs group and starts
the first tab.
If called after a previous `Dialog:tab` call, it marks the end of the previous
tab and starts a new one.

Once started a tab, you can define its content by adding widgets as usual. When
you are done adding tabs, call [Dialog:endtabs](#dialogendtabs).

* `id`: Identifier for this tab. If you specify it, you can use it in
  [Dialog:endtabs](#dialogendtabs) to reference the selected tab. This value
  will be used also when asking for the selected tab through
  [Dialog.data](#dialogdata).
* `text`: Text to display on the tab.
* `onclick`: Function to be called when the tab is pressed. It receives a
  parameter that you can use to get the pressed tab:
    ```lua
    { onclick=function(ev)
         print("pressed tab: " .. ev.tab)
      end }
    ```
Does not support the following common properties: label, hexpand, vexpand.
These can be specified at [Dialog:endtabs](#dialogendtabs).

## Dialog:endtabs()

```lua
local dlg = Dialog()
dlg:endtabs{ id=string,
             selected=string,
             align=integer,
             onchange=function }
```

Marks the end of both the last tab and the group of tabs to which it belongs.

* `id`: Identifier for this tabs widget. [Dialog.data](#dialogdata)
  will contain a field named as this id, which will return the value
  of the currently selected tab's `id`.
* `align`: Horizontal and vertical alignment/placement of the tabs
  selector specified with [Align](align.md#align) values. Its default
  value is `{ align=Align.CENTER|Align.TOP }`.
* `onchange`: Function to be called when the tab is changed. It receives a
  parameter that you can use to get the selected tab:
    ```lua
    { onchange=function(ev)
         print("selected tab: " .. ev.tab)
      end }
    ```

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

## Dialog:canvas()

```lua
local dlg = Dialog()
dlg:canvas{ id=string,
            width=integer,
            height=integer,
            autoscaling=boolean,
            onpaint=function(ev) ... end,
            onkeydown=function(ev) ... end,
            onkeyup=function(ev) ... end,
            onmousemove=function(ev) ... end,
            onmousedown=function(ev) ... end,
            onmouseup=function(ev) ... end,
            ondblclick=function(ev) ... end,
            onwheel=function(ev) ... end,
            ontouchmagnify=function(ev) ... end }
```

The Canvas widget provides several events to create an interactive
experience with the user:

* `onpaint`: A function that receives an event with [a GraphicsContext
  (`ev.context`)](graphicscontext.md#graphicscontext) to paint on.
* `onkeydown`/`onkeyup`: Key events when a key is pressed or released.
  If a canvas widget handles these events, it will receive the
  keyboard focus when it's clicked. The `ev` event is a
  [KeyEvent](keyevent.md).
* `onmousemove`/`onmousedown`/`onmouseup`/`onwheel`: Mouse events when
  the mouse is moved over the canvas, a button is pressed
  (`onmousedown`), a button is released (`onmouseup`), or the mouse
  wheel moved (`onwheel`). The `ev` event is a
  [MouseEvent](mouseevent.md).
* `ontouchmagnify`: Touch event generated when a pinch gesture is done
  in the trackpad to zoom in or out. The `ev` event is a
  [TouchEvent](touchevent.md).

The `autoscaling` property allows the script developer to draw on the GraphicsContext
received in the canvas's onpaint event without worrying about the current UI scale
setting. For instance, you can draw a 20[px]x30[px] rectangle in the canvas's GraphicsContext and it
will be displayed the same at any UI scale. This property is enabled by default if omitted, so if
you don't need it you must explicitly set it to false.

## Dialog:repaint()

```lua
dlg:repaint()
```

Will call `onpaint` event of all [canvases](#dialogcanvas) and update the
dialog pixels on the screen.
