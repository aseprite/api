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
   information, and save other documents from it. Examples: Create
   JSON/XML files from the internal sprite structure, or extract parts
   of the rendered/composed sprite into other PNG files, create
   customized sprite sheets, texture atlases, etc.

1. Hooks: For people that want to execute a script when some event in
   Aseprite happens. Examples: Trigger a specific script when a
   document is saved, e.g. to save x2, x4, x8 versions, export the
   sprite to png automatically, etc.

1. Plugins: For people that want to extend Aseprite
   functionality. Examples: Add a new command, tool, editor state, extra
   information in `.ase` files, customized color picker, etc.

These items are ordered by complexity. The API, maintenance, and
backward compatibility problems increase from the first point to the
last one.
