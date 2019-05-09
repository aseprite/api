# Version

Represents a version number and provides an easy way to compare if the
[`app.version`](app.md#appversion) is greater or equal than a specific
expected version. Example:

```lua
if app.version >= Version("1.2.10-beta4") then
  ...
end
```

## Version()

```lua
local v = Version("1.2.10")
```

You can create a new version from a string. Then access each field

## Version.major

```lua
local v = Version("1.2.9")
assert(v.major == 1)

v = Version("2")
assert(v.major == 2)
```

Returns the first number of the version.

## Version.minor

```lua
local v = Version("1.2.9")
assert(v.minor == 2)

v = Version("2")
assert(v.minor == 0)
```

Returns the second number of the version.

## Version.patch

```lua
local v = Version("1.2.9")
assert(v.patch == 9)

v = Version("2")
assert(v.patch == 0)
```

Returns the third number of the version.

## Version.prereleaseLabel

```lua
local v = Version("1.2.10-beta4")
assert(v.prereleaseLabel == "beta")

v = Version("2")
assert(v.prereleaseLabel == "")
```

Returns the pre-release label/keyword. For official releases it's an
empty string, in other cases it might be `"alpha"`, `"beta"`, `"dev"`, etc.

## Version.prereleaseNumber

```lua
local v = Version("1.2.10-beta4")
assert(v.prereleaseNumber == 4)

v = Version("2")
assert(v.prereleaseNumber == 0)
```

Returns the pre-release version.
