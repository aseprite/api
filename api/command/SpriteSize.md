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

* `ui`: Shows the dialog on the screen, true by default. Set to false for automatic sprite size modification without asking to the user for the change.
* `width`: Final sprite width. Default value is the current sprite width.
* `height`: Final sprite height. Default value is the current sprite height.
* `scale`: Bidimensional scale factor per unit (1.0 = same original sprite size). Default value is `1.0`.
* `scaleX`: horizontal scale factor per unit. Default value is `1.0`.
* `scaleY`: Vertical scale factor per unit. Default value is `1.0`.
* `lockRatio`: Final sprite aspect ratio is locked when it is `true`. Default value is `false`.
* `method`: Resize algorithm method to be used. Default is `nearest` (for Nearest Neighbor), alternatives: `bilinear`
and `rotSprite`.

Note: we should be able to use image "i", but at the moment image IDs change after a SpriteSize.
```local s = Sprite(1, 1)
local cel = app.activeCel
local i = cel.image
local r = Color(255, 0, 0).rgbaPixel

i:drawPixel(0, 0, r)

expect_img(i, { r }) -- OK

app.command.SpriteSize{ ui = false, scaleX = 2 }

expect_img(i, { r,r }) --it will fail```

So, to make it works, we will use "cel.image" instead of "i":

```local s = Sprite(1, 1)
local cel = app.activeCel
local r = Color(255, 0, 0).rgbaPixel

cel.image:drawPixel(0, 0, r)

expect_img(cel.image, { r }) -- OK

app.command.SpriteSize{ ui = false, scaleX = 2 }

expect_img(cel.image, { r,r }) --it will pass```

This issue will be fixed in a future.