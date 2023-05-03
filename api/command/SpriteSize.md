# SpriteSize

```lua
app.command.SpriteSize {
  ui=true,
  width=100,
  height=100,
  scale=1.0,
  scaleX=1.0,
  scaleY=1.0,
  lockRatio=false,
  method="nearest"
}
```

* `ui`: Shows the dialog on the screen, `true` by default. Set to `false` to modify the sprite size without asking to the user.
* `width`: Final sprite width. Current sprite width by default.
* `height`: Final sprite height. Current sprite height by default.
* `scale`: Bidimensional scale factor per unit (1.0 = same original sprite size). `1.0` by default.
* `scaleX`: horizontal scale factor per unit. `1.0` by default.
* `scaleY`: Vertical scale factor per unit. `1.0` by default.
* `lockRatio`: Final sprite aspect ratio is locked when it is `true`.`false` by default.
* `method`: Resize algorithm method to be used. `"nearest"` by default (Nearest Neighbor), alternatives: `"bilinear"` and `"rotSprite"`.

Known issue: On the following code, we have a variable `i` pointing to the `cel.image`. After the `app.command.SpriteSize` execution, `i` doesn't longer points to original image. Finally, `print(i.width)` will fail.

```lua
local s = Sprite(1, 1)
local cel = app.cel
local i = cel.image

app.command.SpriteSize{ ui = false, scaleX = 2 }

print(i.width) -- it will fail: ...attempt to index a nil value (global 'i')
```

So, to make it works, we have to use `cel.image` instead of `i`:

```lua
local s = Sprite(1, 1)
local cel = app.cel

app.command.SpriteSize{ ui = false, scaleX = 2 }

print(cel.image.width) -- it will print "2"
```
Another way, using `i`, and get again the `cel.image` after `app.command.SpriteSize`:

```lua
local s = Sprite(1, 1)
local cel = app.cel
local i = cel.image

app.command.SpriteSize{ ui = false, scaleX = 2 }
i = cel.image  -- We have to get the image again
print(i.width) -- it will print "2"
```

This issue will be fixed soon.
