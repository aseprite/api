# Site

This is an object that saves the active state of the editor in a
specific moment. Which active sprite, layer, frame, cel, image,
etc. where in a specific moment.

If you save the object:

```lua
local site = app.site
```

The `site` object will not be updated if the active sprite is
modified.

## Site.sprite

Gets the [active sprite](app.md#appactivesprite) at the time the
site object was created.

## Site.layer

Gets the [active layer](app.md#appactivelayer) at the time the site
object was created.

## Site.cel

Gets the [active cel](app.md#appactivecel) at the time the site
object was created.

## Site.frame

Gets the [active frame](app.md#appactiveframe) at the time the site
object was created.

## Site.frameNumber

Gets the active frame number (an integer value, 1 is the first frame).
Same as [`app.site.frame.frameNumber`](#siteframe).

## Site.image

Gets the [active image](app.md#appactiveimage) at the time the site
object was created.
