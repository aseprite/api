# app.command

```lua
app.command.CommandName()
app.command.CommandName { param1=value1, param2=value2, ... }
```

Executes the given command named `CommandName` with the given
parameters.

* app.command.About
* [app.command.AddColor](command/AddColor.md#addcolor)
* app.command.AdvancedMode
* app.command.AutocropSprite
* app.command.BackgroundFromLayer
* [app.command.BrightnessContrast](command/BrightnessContrast.md#brightnesscontrast)
* app.command.Cancel
* [app.command.CanvasSize](command/CanvasSize.md#canvassize)
* [app.command.CelOpacity](command/CelOpacity.md#celopacity)
* app.command.CelProperties
* app.command.ChangeBrush
* app.command.ChangeColor
* [app.command.ChangePixelFormat](command/ChangePixelFormat.md#changepixelformat)
* app.command.ClearCel
* app.command.Clear
* app.command.CloseAllFiles
* app.command.CloseFile
* [app.command.ColorCurve](command/ColorCurve.md#colorcurve)
* app.command.ColorQuantization
* app.command.ContiguousFill
* [app.command.ConvolutionMatrix](command/ConvolutionMatrix.md#convolutionmatrix)
* app.command.CopyCel
* [app.command.CopyColors](command/CopyColors.md#copycolors)
* app.command.CopyMerged
* app.command.Copy
* app.command.CropSprite
* app.command.Cut
* app.command.DeselectMask
* [app.command.Despeckle](command/Despeckle.md#despeckle)
* app.command.DeveloperConsole
* app.command.DiscardBrush
* app.command.DuplicateLayer
* app.command.DuplicateSprite
* app.command.DuplicateView
* app.command.Exit
* [app.command.ExportSpriteSheet](command/ExportSpriteSheet.md#exportspritesheet)
* [app.command.ExportTileset](command/ExportTileset.md#exporttileset)
* app.command.Eyedropper
* app.command.Fill
* app.command.FitScreen
* app.command.FlattenLayers
* app.command.Flip
* app.command.FrameProperties
* app.command.FrameTagProperties
* app.command.FullscreenPreview
* app.command.GotoFirstFrameInTag
* app.command.GotoFirstFrame
* app.command.GotoFrame
* app.command.GotoLastFrameInTag
* app.command.GotoLastFrame
* app.command.GotoNextFrameWithSameTag
* app.command.GotoNextFrame
* app.command.GotoNextLayer
* app.command.GotoNextTab
* app.command.GotoPreviousFrameWithSameTag
* app.command.GotoPreviousFrame
* app.command.GotoPreviousLayer
* app.command.GotoPreviousTab
* app.command.GridSettings
* app.command.Home
* [app.command.HueSaturation](command/HueSaturation.md#huesaturation)
* [app.command.ImportSpriteSheet](command/ImportSpriteSheet.md#importspritesheet)
* [app.command.InvertColor](command/InvertColor.md#invertcolor)
* app.command.InvertMask
* app.command.KeyboardShortcuts
* app.command.Launch
* app.command.LayerFromBackground
* app.command.LayerLock
* [app.command.LayerOpacity](command/LayerOpacity.md#layeropacity)
* app.command.LayerProperties
* app.command.LayerVisibility
* app.command.LinkCels
* app.command.LoadMask
* app.command.LoadPalette
* app.command.MaskAll
* app.command.MaskByColor
* app.command.MaskContent
* app.command.MergeDownLayer
* app.command.ModifySelection
* app.command.MoveCel
* [app.command.MoveColors](command/MoveColors.md#movecolors)
* [app.command.MoveMask](command/MoveMask.md#movemask)
* app.command.NewBrush
* [app.command.NewFile](command/NewFile.md#newfile)
* app.command.NewFrameTag
* app.command.NewFrame
* [app.command.NewLayer](command/NewLayer.md#newlayer)
* app.command.NewSpriteFromSelection
* app.command.OpenBrowser
* app.command.OpenFile
* app.command.OpenGroup
* app.command.OpenInFolder
* app.command.OpenScriptFolder
* app.command.OpenWithApp
* [app.command.Options](command/Options.md#options)
* [app.command.Outline](command/Outline.md#outline)
* app.command.PaletteEditor
* app.command.PaletteSize
* app.command.PasteText
* app.command.Paste
* app.command.PixelPerfectMode
* app.command.PlayAnimation
* app.command.PlayPreviewAnimation
* app.command.Redo
* app.command.Refresh
* app.command.RemoveFrameTag
* app.command.RemoveFrame
* app.command.RemoveLayer
* app.command.RemoveSlice
* app.command.RepeatLastExport
* [app.command.ReplaceColor](command/ReplaceColor.md#replacecolor)
* app.command.ReselectMask
* app.command.ReverseFrames
* app.command.Rotate
* app.command.RunScript
* [app.command.SaveFile](command/SaveFile.md#savefile)
* [app.command.SaveFileAs](command/SaveFile.md#savefile)
* [app.command.SaveFileCopyAs](command/SaveFile.md#savefile)
* app.command.SaveMask
* app.command.SavePalette
* app.command.ScrollCenter
* app.command.Scroll
* app.command.SelectTile
* app.command.SelectionAsGrid
* app.command.SetColorSelector
* [app.command.SetInkType](command/SetInkType.md)
* app.command.SetLoopSection
* app.command.SetPaletteEntrySize
* app.command.SetPalette
* app.command.SetSameInk
* app.command.ShowAutoGuides
* app.command.ShowBrushPreview
* app.command.ShowExtras
* app.command.ShowGrid
* app.command.ShowLayerEdges
* app.command.ShowOnionSkin
* app.command.ShowPixelGrid
* app.command.ShowSelectionEdges
* app.command.ShowSlices
* app.command.SliceProperties
* app.command.SnapToGrid
* app.command.SpriteProperties
* [app.command.SpriteSize](command/SpriteSize.md)
* app.command.Stroke
* app.command.SwitchColors
* app.command.SymmetryMode
* app.command.TiledMode
* app.command.Timeline
* app.command.TogglePreview
* app.command.ToggleTimelineThumbnails
* app.command.UndoHistory
* app.command.Undo
* app.command.UnlinkCel
* app.command.Zoom

If you cannot find a specific command, you might like to give a look at the
[gui.xml](https://github.com/aseprite/aseprite/blob/main/data/gui.xml)
file which contains the definitions of menus / commands + the parameters.

To figure out the parameters of an undocumented command, you can:

1. Choose a command (the `CommandName` part of `app.command.CommandName`) from
   [gui.xml](https://github.com/aseprite/aseprite/blob/main/data/gui.xml) file
   ( `<key command="CommandName" ...>` or `<item command="CommandName" ...>`)
1. If those `<key>...</key>` or `<item>...</item>` XML elements contain children elements
   like `<param name="param-name1" value="param-value2" />`
   you can specify those parameters in Lua between `{ ... }`, for example:
   ```lua
   app.command.CommandName { ["param-name1"]="param-value1", ["param-name2"]="param-value2" }
   ```

Another alternative is looking to the Aseprite source code:

1. Choose the command you want to use and find its counterpart `.cpp` file
   in [src/app/commands/](https://github.com/aseprite/aseprite/tree/main/src/app/commands)
   (e.g. `app.command.CropSprite` has the file `cmd_crop.cpp`)
1. Find all places in the file where `params.get` is used, the strings
   in that function are the parameter names you need to use.
1. When setting the parameters, you'll want to write the parameters as
   below because Lua does not accept hyphens in identifiers.
   ```lua
   app.command.CommandName { ["parameter-name"]="value", ["other-parameter-name"]="otherValue" }
   ```
