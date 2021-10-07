# Events

A collection of listeners for specific events. Available for
[`App.events`](app.md#appevents) and
[`Sprite.events`](sprite.md#spriteevents).

With this property you can associate (or disassociate) a function to a
specific event.

## Events:on()

```lua
local listenerCode = events:on(eventName, function)
```

Connects the given `function` (2nd argument) with the given event by
`eventName` (a `string`, the event name/code/identifier). When the
event happens in the future the function will be called automatically.
This is like the `function` starts "listening" the event.

The returned `listenerCode` is a numeric value that indicates the
connection between the event and the function. You can use this value
in [`Events.off()`](#eventsoff) to stop listening/break the connection
with the event.

E.g.

```lua
app.events:on('sitechange',
  function()
    print('app.site has changed')
  end)
```

## Events:off()

```lua
events:off(function)
events:off(listenerCode)
```

Disconnects the given `function` from all events in the object, or
stops/breaks only the specific connection identified by `listenerCode`
(the code returned by [`Events:on()`](#eventson)).

```lua
local function onSiteChange() ... end
app.events:on('sitechange', onSiteChange)
app.events:off(onSiteChange)
```
