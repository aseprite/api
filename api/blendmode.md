# BlendMode

Blend modes defines how the colors should be mixed when two images overlaps. Used in [Image:drawImage()](image.md#imagedrawimage) as input argument.

Background sample // sample with blending applied

![background](image/background.png)
![duck](image/duck.png)

## BlendMode.NORMAL

Mix the background colors with the blending image proportionally to its alpha values. Full transparent pixels will show the background.

![normal_blend](image/normal_blend.png)

## BlendMode.SRC

A simple copy/paste of the blending image to the background.

![normal_blend](image/src_blend.png)

## BlendMode.MULTIPLY

![multiply_blend](image/multiply_blend.png)

## BlendMode.SCREEN

![screen_blend](image/screen_blend.png)

## BlendMode.OVERLAY

![overlay_blend](image/overlay_blend.png)

## BlendMode.DARKEN

![darken_blend](image/darken_blend.png)

## BlendMode.LIGHTEN

![lighten_blend](image/lighten_blend.png)

## BlendMode.COLOR_DODGE

![color_dodge_blend](image/color_dodge_blend.png)

## BlendMode.COLOR_BURN

![color_burn_blend](image/color_burn_blend.png)

## BlendMode.HARD_LIGHT

![hard_light_blend](image/hard_light_blend.png)

## BlendMode.SOFT_LIGHT

![soft_light_blend](image/soft_light_blend.png)

## BlendMode.DIFFERENCE

![difference_blend](image/difference_blend.png)

## BlendMode.EXCLUSION

![exclusion_blend](image/exclusion_blend.png)

## BlendMode.HSL_HUE

![hue_blend](image/hue_blend.png)

## BlendMode.HSL_SATURATION

![saturation_blend](image/saturation_blend.png)

## BlendMode.HSL_COLOR

![color_blend](image/color_blend.png)

## BlendMode.HSL_LUMINOSITY

![luminosity_blend](image/luminosity_blend.png)

## BlendMode.ADDITION

![addition_blend](image/addition_blend.png)

## BlendMode.SUBTRACT

![subtract_blend](image/subtract_blend.png)

## BlendMode.DIVIDE

![divide_blend](image/divide_blend.png)