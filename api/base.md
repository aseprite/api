# Base library

## assert()

```lua
assert(condition)
```

Prints an error message when `condition` is `false` and stops the
execution of the script. This method is used for unit-testing.

## print()

```lua
print(object)
print(object1, object2, ...)
```

Prints the given objects (generally strings) into the console (the
Terminal if we're executing the script in `--batch` or `--shell`
mode).
