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

Gets the [active sprite](app.md#appsprite) at the time the site object
was created.

## Site.layer

Gets the [active layer](app.md#applayer) at the time the site object
was created.

## Site.cel

Gets the [active cel](app.md#appcel) at the time the site object was
created.

## Site.frame

Gets the [active frame](app.md#appframe) at the time the site object
was created.

## Site.frameNumber

Gets the active frame number (an integer value, 1 is the first frame).
Same as [`app.site.frame.frameNumber`](#siteframe).

## Site.image

Gets the [active image](app.md#appimage) at the time the site object
was created.

## Site.tilemapMode

Gets [TilemapMode](tilemapmode.md#tilemapmode). On non-tilemap layers, this field returns 0.

## Site.tilesetMode

Gets [TilesetMode](tilesetmode.md#tilesetmode). On non-tilemap layers, this field returns 0.