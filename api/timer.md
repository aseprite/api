# Timer

The Timer class can be used to execute a function periodically.

Example to create a function that is called:

```lua
local timer = Timer{
  interval=5.0,
  ontick=function()
    print('Each 5 seconds')
  end }
timer:start()
```

Or a function that is called just once after one second:

```lua
local timer
timer = Timer{
  interval=1.0,
  ontick=function()
    print('Called')
    timer:stop()
  end }
timer:start()
```

## Timer()

```lua
local timer = Timer{ interval=number,
                     ontick=function }
```

Creates a new timer.

* `interval`: Number of seconds to wait for the first/next call. You
  can specify decimal numbers, e.g. `interval=1.0 / 60.0` to call the
  function 60 times per second, etc.
* `ontick`: Function that is called each time the specified number of
  seconds ellapses.

## Timer:start()

Starts the timer.

## Timer:stop()

Stops the timer.

## Timer.interval

Returns the interval of this specific timer (in seconds).

## Timer.isRunning

Returns true if the timer is running.
