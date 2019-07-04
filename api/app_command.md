# app.command

```lua
app.command.CommandName()
app.command.CommandName { param1=value1, param2=value2, ... }
```

Executes the given command named `CommandName` with the given
parameters.

* `app.command.About`
* `app.command.AddColor`
* `app.command.AdvancedMode`
* `app.command.AutocropSprite`
* `app.command.BackgroundFromLayer`
* `app.command.BrightnessContrast`
* `app.command.Cancel`
* `app.command.CanvasSize`
* `app.command.CelOpacity`
* `app.command.CelProperties`
* `app.command.ChangeBrush`
* `app.command.ChangeColor`
* `app.command.ChangePixelFormat`
* `app.command.ClearCel`
* `app.command.Clear`
* `app.command.CloseAllFiles`
* `app.command.CloseFile`
* `app.command.ColorCurve`
* `app.command.ColorQuantization`
* `app.command.ContiguousFill`
* `app.command.ConvolutionMatrix`
* `app.command.CopyCel`
* `app.command.CopyMerged`
* `app.command.Copy`
* `app.command.CropSprite`
* `app.command.Cut`
* `app.command.DeselectMask`
* `app.command.Despeckle`
* `app.command.DeveloperConsole`
* `app.command.DiscardBrush`
* `app.command.DuplicateLayer`
* `app.command.DuplicateSprite`
* `app.command.DuplicateView`
* `app.command.Exit`
* [`app.command.ExportSpriteSheet`](command/ExportSpriteSheet.md)
* `app.command.Eyedropper`
* `app.command.Fill`
* `app.command.FitScreen`
* `app.command.FlattenLayers`
* `app.command.Flip`
* `app.command.FrameProperties`
* `app.command.FrameTagProperties`
* `app.command.FullscreenPreview`
* `app.command.GotoFirstFrameInTag`
* `app.command.GotoFirstFrame`
* `app.command.GotoFrame`
* `app.command.GotoLastFrameInTag`
* `app.command.GotoLastFrame`
* `app.command.GotoNextFrameWithSameTag`
* `app.command.GotoNextFrame`
* `app.command.GotoNextLayer`
* `app.command.GotoNextTab`
* `app.command.GotoPreviousFrameWithSameTag`
* `app.command.GotoPreviousFrame`
* `app.command.GotoPreviousLayer`
* `app.command.GotoPreviousTab`
* `app.command.GridSettings`
* `app.command.Home`
* `app.command.HueSaturation`
* `app.command.ImportSpriteSheet`
* `app.command.InvertColor`
* `app.command.InvertMask`
* `app.command.KeyboardShortcuts`
* `app.command.Launch`
* `app.command.LayerFromBackground`
* `app.command.LayerLock`
* `app.command.LayerOpacity`
* `app.command.LayerProperties`
* `app.command.LayerVisibility`
* `app.command.LinkCels`
* `app.command.LoadMask`
* `app.command.LoadPalette`
* `app.command.MaskAll`
* `app.command.MaskByColor`
* `app.command.MaskContent`
* `app.command.MergeDownLayer`
* `app.command.ModifySelection`
* `app.command.MoveCel`
* `app.command.MoveMask`
* `app.command.NewBrush`
* [`app.command.NewFile`](command/NewFile.md)
* `app.command.NewFrameTag`
* `app.command.NewFrame`
* `app.command.NewLayer`
* `app.command.NewSpriteFromSelection`
* `app.command.OpenBrowser`
* `app.command.OpenFile`
* `app.command.OpenGroup`
* `app.command.OpenInFolder`
* `app.command.OpenScriptFolder`
* `app.command.OpenWithApp`
* `app.command.Options`
* `app.command.PaletteEditor`
* `app.command.PaletteSize`
* `app.command.PasteText`
* `app.command.Paste`
* `app.command.PixelPerfectMode`
* `app.command.PlayAnimation`
* `app.command.PlayPreviewAnimation`
* `app.command.Redo`
* `app.command.Refresh`
* `app.command.RemoveFrameTag`
* `app.command.RemoveFrame`
* `app.command.RemoveLayer`
* `app.command.RemoveSlice`
* `app.command.RepeatLastExport`
* `app.command.ReplaceColor`
* `app.command.ReselectMask`
* `app.command.ReverseFrames`
* `app.command.Rotate`
* `app.command.RunScript`
* `app.command.SaveFileAs`
* `app.command.SaveFileCopyAs`
* `app.command.SaveFile`
* `app.command.SaveMask`
* `app.command.SavePalette`
* `app.command.ScrollCenter`
* `app.command.Scroll`
* `app.command.SelectTile`
* `app.command.SelectionAsGrid`
* `app.command.SetColorSelector`
* `app.command.SetInkType`
* `app.command.SetLoopSection`
* `app.command.SetPaletteEntrySize`
* `app.command.SetPalette`
* `app.command.SetSameInk`
* `app.command.ShowAutoGuides`
* `app.command.ShowBrushPreview`
* `app.command.ShowExtras`
* `app.command.ShowGrid`
* `app.command.ShowLayerEdges`
* `app.command.ShowOnionSkin`
* `app.command.ShowPixelGrid`
* `app.command.ShowSelectionEdges`
* `app.command.ShowSlices`
* `app.command.SliceProperties`
* `app.command.SnapToGrid`
* `app.command.SpriteProperties`
* `app.command.SpriteSize`
* `app.command.Stroke`
* `app.command.SwitchColors`
* `app.command.SymmetryMode`
* `app.command.TiledMode`
* `app.command.Timeline`
* `app.command.TogglePreview`
* `app.command.ToggleTimelineThumbnails`
* `app.command.UndoHistory`
* `app.command.Undo`
* `app.command.UnlinkCel`
* `app.command.Zoom`

If you cannot find a specific command, you might like to give a look at the
[gui.xml](https://github.com/aseprite/aseprite/blob/master/data/gui.xml)
file which contains the definitions of menus / commands + the parameters.

To figure out the parameters of a script if you can't find them:
1. Choose the command you want to find and find it's counterpart cpp file in [commands](https://github.com/aseprite/aseprite/tree/master/src/app/commands). For example: `app.command.CropSprite` has the file `cmd_crop.cpp`
2. Find all places in the file where `params.get` is used, the strings in that function are the parameter names you need to use.
3. When settings the parameters, you'll want to write the parameters as below because Lua does not accept hyphens in identifiers.
```lua 
app.command.CommandName { ["parameter-name"] = value, ["other-parameter-name"] = otherValue }
```
