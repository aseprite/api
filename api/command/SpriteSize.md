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
