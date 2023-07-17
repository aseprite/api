# json

Since **Aseprite v1.3-rc5** you have this `json` global namespace. It
provides a couple of functions to decode JSON objects from strings to
Lua objects/tables and viceversa.

## json.decode()

```lua
local jsonObj = json.decode(jsonText)
```

Parses the given `jsonText` and returns a Lua table-like object
`jsonObj` that represents the given data.

Examples:

```lua
local obj = json.decode('{"a":true,"b":5,"c":[1,3,9]}')
assert(#obj == 3)
assert(obj.a == true)
assert(obj.b == 5)
assert(#obj.c == 3)
assert(obj.c[1] == 1)
assert(obj.c[2] == 3)
assert(obj.c[3] == 9)
```

## json.encode()

```lua
local text = json.encode(luaTable)
local text = json.encode(jsonObj) -- same as tostring(jsonObj)
```

Converts the given Lua-table into a JSON text.

Example:

```lua
local text = json.encode({ a=4, b=true, c="name", d={1,8,{a=2}} })
assert(text == '{"a": 4, "b": true, "c": "name", "d": [1, 8, {"a": 2}]}')
```
