# Uuid

Represents an UUID (*Universally Unique IDentifier*), a 16-bytes
unique identifier.

You can compare UUIDs, convert them to a string of the
`"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"` 36-chars format, or get each
of byte using the `__index` Lua operator. Example:

```lua
local u = Uuid()
assert(u == Uuid(tostring(u)))
assert(tostring(u):sub(1, 2) == string.format("%02x", u[1]))
```

## Uuid()

```lua
local u = Uuid()
local v = Uuid("74341b56-4f7f-4ab1-9495-58cf5bce0e1c") -- e.g.
```

You can create a new random UUID using `Uuid()` or a UUID
representation of the given 36-chars string.
