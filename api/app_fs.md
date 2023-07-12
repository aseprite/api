# app.fs

A set of function to handle file names and the file system.

# Path & File Name Manipulation

## app.fs.pathSeparator

```lua
local fn = "path" .. app.fs.pathSeparator .. "filename.png"
```

Returns the preferred path separator of the current platform, it is
`/` on macOS and Linux, and `\` on Windows. Preferably you should use
[app.fs.joinPath()](#appfsjoinpath).

Example:

```lua
local sep = app.fs.pathSeparator
local fn = "path" .. sep .. "filename.png"
print(fn)
```

Will print `path/filename.png` on macOS or Linux, and `path\filename.png` on Windows.

## app.fs.filePath()

```lua
local pathPart = app.fs.filePath(fn)
```

Returns the path/directory part (as a string) of the given filename `fn`.

## app.fs.fileName()

```lua
local fileName = app.fs.fileName(fn)
```

Returns the file name (including the extension part) of the given filename `fn`.

## app.fs.fileExtension()

```lua
local extension = app.fs.fileExtension(fn)
```

Returns the file extension (without including the `.`) of the given
filename `fn`. For example:

```lua
print(app.fs.fileExtension("path/file.png"))
```

Prints `png`.

## app.fs.fileTitle()

```lua
local title = app.fs.fileTitle(fn)
```

Returns the file title (without including the path nor the extension)
of the given filename `fn`. For example:

```lua
print(app.fs.fileTitle("path/file.png"))
```

Prints `file`.

## app.fs.filePathAndTitle()

```lua
local title = app.fs.filePathAndTitle(fn)
```

Returns the file path [joined](#appfsjoinpath) with the title (without
including the extension) of the given filename `fn`. For example:

```lua
print(app.fs.filePathAndTitle("path/file.png"))
```

Prints `path/file`.

## app.fs.normalizePath()

Returns the file path converted to a canonical form for the current platform.

Example:

```lua
print(app.fs.normalizePath("//home//user//path"))
```

Will print as `/home/user/path` on macOS or Linux, and `C:\home\user\path` on Windows.

## app.fs.joinPath()

Can accept any number of string arguments to join together with the path separator for the current platform.

```lua
local path = app.fs.joinPath("path1", "path2")
```

Returns `path1/path2` on macOS or Linux, and `path1\path2` on Windows.

# Special Folders

## app.fs.currentPath

Returns the path the Aseprite executable was launched from.

## app.fs.appPath

Returns the installation path of Aseprite for the current platform.

## app.fs.tempPath

Returns the path for temporary files for the current platform.

On macOS or Linux it will be `/tmp`, and Windows it will look like `C:\Users\username\AppData\Local\Temp\`.

## app.fs.userDocsPath

Returns the current user's Documents path for the current platform.

Depending on the platform, this may return the user's home directory.

## app.fs.userConfigPath

Returns the current user's Aseprite configuration path for the current platform.

You can learn about the specific location of this folder [from the Aseprite documentation](https://www.aseprite.org/docs/preferences-folder/).

# File System Access

## app.fs.isFile()

```lua
local exists = app.fs.isFile(fn)
```

Returns true if the given filename `fn` is a file.

## app.fs.isDirectory()

```lua
local exists = app.fs.isDirectory(fn)
```

Returns true if the given filename `fn` is a directory.

## app.fs.fileSize()

```lua
local size = app.fs.fileSize(fn)
```

Returns the file size of the given filename `fn`.

## app.fs.listFiles()

```lua
local table = app.fs.listFiles(path)
```

Returns a list of files in the given directory `path`. The returned
value is a table where each element is a file name, each file name is
relative to the given `path`, they are not full path file names. In
case that you want to get a list of full file names you can do
something like this:

```lua
local dir = ...
for _,filename in pairs(app.fs.listFiles(dir)) do
  local fullFilename = app.fs.joinPath(dir, filename)
  ...
end
```

## app.fs.makeDirectory()

```lua
app.fs.makeDirectory(path)
```

Create one directory.

Returns `true` if the directory was created.

## app.fs.makeAllDirectories()

```lua
local result = app.fs.makeAllDirectories(path)
```

Create all directories needed to access to the `path`, so path could
be `dir1/dir2/dir3` and the whole hierarchy of directories will be
created.

Returns `true` if all the directories were created.

## app.fs.removeDirectory()

```lua
app.fs.removeDirectory(path)
```

Remove the given directory (it must be empty).

Returns `true` if the directory was removed (or is already removed).
