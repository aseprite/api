# app.os

A set of function to get properties about the running Operating System
platform.

## app.os.name

```lua
local name = app.os.name
```

Returns the platform name. It can be `Windows`, `macOS`, or `Linux`.

## app.os.version

Returns an [`Version`](version.md#version) with the Windows or macOS
version. It's just `0.0.0` on Linux.

## app.os.fullName

Returns the full platform name with its version. On Linux returns the
distribution name with its specific version.

Some examples: `Windows NT 10.0.22631`, `macOS 14.4.1`, `Pop!_OS 22.04 LTS`, etc.

## app.os.windows
## app.os.macos
## app.os.linux
## app.os.x64
## app.os.x86
## app.os.arm64

These are `true`/`false` properties if we are running in the given
platform. For example:

```lua
if app.os.windows then
  print("Running on Windows")
elseif app.os.macos then
  if app.os.arm64 then
    print("Running on Apple Silicon")
  end
end
```
