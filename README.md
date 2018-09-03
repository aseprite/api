# Aseprite API

This is the scripting API for Aseprite. Since Aseprite v1.2.10 you
will be able to create scripts with [Lua](https://www.lua.org/).

You can find some tests/examples for this API
[here](https://github.com/aseprite/tests/tree/master/scripts).

* Lua libraries
  * [Basic Functions](https://www.lua.org/manual/5.3/manual.html#6.1)
  * [Coroutine Manipulation](https://www.lua.org/manual/5.3/manual.html#6.2)
  * [String Manipulation](https://www.lua.org/manual/5.3/manual.html#6.4)
  * [UTF-8 Support](https://www.lua.org/manual/5.3/manual.html#6.5)
  * [Table Manipulation](https://www.lua.org/manual/5.3/manual.html#6.6)
  * [Mathematical Functions](https://www.lua.org/manual/5.3/manual.html#6.7)
  * [Operating System Facilities](https://www.lua.org/manual/5.3/manual.html#6.9)
    * Some functions are not available yet (like `os.execute`,
      `os.remove`, `os.rename`, `os.exit`, `os.tmpname`)
  * [The Debug Library](https://www.lua.org/manual/5.3/manual.html#6.10)
* Globals namespaces
  * [app](api/app.md)
  * [app.pixelColor](api/pixelcolor.md)
* Constants
  * [ColorMode](api/colormode.md)
* Classes/objects
  * [Image](api/image.md)
  * [Point](api/point.md)
  * [Rectangle](api/rectangle.md)
  * [Selection](api/selection.md)
  * [Size](api/size.md)
  * [Sprite](api/sprite.md)
