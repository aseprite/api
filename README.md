# Aseprite Scripting API Draft

This is an experimental repository to create a scripting API for
Aseprite. We'll use JavaScript as scripting language and
[duktape.org](http://duktape.org/) as the scripting engine.

## Use Cases

What we should be able to do with this API?  We can identify some use
cases:

1. Scripts for testing: To create scripts to test end-user
   capabilities.

1. Scripts: For people that want to open a sprite, extract its
   information, and save other sprites from it. Examples: Create
   JSON/XML files from the internal sprite structure, or extract parts
   of the rendered/composed sprite into other PNG files, create
   customized sprite sheets, texture atlases, etc.

1. Hooks: For people that want to execute a script when some event in
   Aseprite happens. Examples: Trigger a specific script when a sprite
   is saved, e.g. to save x2, x4, x8 versions, export the sprite to
   png automatically, etc.

1. Plugins: For people that want to extend Aseprite
   functionality. Examples: Add a new command, tool, editor state, extra
   information in `.ase` files, customized color picker, etc.

These items are ordered by complexity. The API, maintenance, and
backward compatibility problems increase from the first point to the
last one.

## Scripts Examples

Test if a GIF file is converted to RGB correctly:

    var sprite1 = app.sprites.open("test.gif")
    var sprite2 = app.sprites.open({
      "expected0.png", "expected1.png", "expected3.png" })

    // It should call the internal command know as ChangePixelFormat
    sprite2.colorMode = ColorMode.RGB

    // Compare that both sprites are equal (same width, height,
    // color mode, pixels, palettes).
    app.test.expectEqual(sprite2, sprite1)

Create a simple sprite, and focus the second frame (the shown API here
is just an example):

    // Possible API to call commands
    app.commands.NewSprite({
      width: 32,
      height: 32,
      colorMode: ColorMode.RGB,
      background: Color.BLACK
    })
    var sprite = app.activeSprite

    // Alternative API to create sprites?
    var sprite2 = app.sprites.add(32, 32, ColorMode.RGB)

    // Or just?
    var sprite3 = new Sprite(32, 32, ColorMode.RGB)

    var bg = sprite.layers.background()
    sprite.selection.selectAll()
    sprite.selection.clear(new RGBColor(0, 0, 0))

    // Add a transparent layer
    var layer1 = sprite.layers.add("Layer 1")

    // Add a 2nd frame
    var frame2 = sprite.frames.add()
    frame2.duration = 500

    // Show 2nd frame
    app.views(sprite).activeFrame = 2

## Observe Events Examples

Everytime we save an image, save a copy into `path/filename-x2.png`
resizing it to 200%:

    app.events.on('afterSave', function(ev) {
      var sprite = ev.sprite
      var fn = sprite.filename
      fn = fn.path + "/" + fn.title + "x2.png"

      var sprite2 = sprite.duplicate()
      sprite2.resizeSprite(sprite.width*2, sprite.height*2)
      sprite2.saveAs(fn)
      sprite2.close()
    })

## Plugins Examples

It would be great if we could create some kind of plugins.
Some use cases:

* Automate and extend post-Save process. E.g. After we save a
  sprite, this could automatically trigger some extra "Save As"
  commands (to save the image in different sizes) or export a sprite
  sheet automatically.

* Customize sprite sheet import/export process. E.g. To import and/or
  export user defined formats.

## Complex plugins

These examples would require complex low-level APIs (or APIs so hard
to maintenance for dynamic typing scripting languages that it would be
preferred to create them directly on C++):

* Open/save special image/animation/palette formats. Cons: We will
  need a low-level API to write/read files (and
  bytes/words/dwords/etc).

* Create new commands. Pros: Any user could create new commands. Cons:
  We should expose some kind of simplified GUI API.

## Plugins problems

* Maintenance: Keeping backward compatibility in a scripting API to
  create plugins will be a maintenance nightmare. It already was a
  problem when parts of Aseprite were programmed in Lua, and both
  sides were programmed by myself.

* License: As Aseprite is GPL, plugins should be GPL. The alternative
  is to release Aseprite with a dual-license model, so the official
  release could be released under a special EULA were closed-source
  plugins could be used. The interesting part here is that GPL plugins
  couldn't be used in the commercial version. I think that a solution
  could be to release plugins under LGPL or MIT for those who wants to
  create non-commercial open sourced plugins for both versions.

* Store & Security: We don't have the infrastructure (at this point)
  to provide some kind of plugins store, or guarantee third-party
  virus free plugins.
