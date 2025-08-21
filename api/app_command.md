# app.command

```lua
app.command.CommandName()
app.command.CommandName { param1=value1, param2=value2, ... }
```

Executes the given command named `CommandName` with the specified parameters.

* app.command.About <sup>[[UI]](#requiresUI "Requires UI")</sup>
 * Opens the About Aseprite window
* [app.command.AddColor](command/AddColor.md#addcolor "Adds a new color to the palette.")
* app.command.AdvancedMode <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Toggles the application's "Advanced Mode"
* [app.command.AutocropSprite](command/AutocropSprite.md#autocropsprite)
* app.command.BackgroundFromLayer
  * Equivalent to using Convert To -> Background in the Layer's context menu
* [app.command.BrightnessContrast](command/BrightnessContrast.md#brightnesscontrast) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.Cancel
  * Equivalent to pressing the Esc key
* [app.command.CanvasSize](command/CanvasSize.md#canvassize) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.CelOpacity](command/CelOpacity.md#celopacity "Changes the opacity of the active Cel")
* app.command.CelProperties <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Shows the Properties dialog for the active Cel
* [app.command.ChangeBrush](command/ChangeBrush.md#changebrush "Changes the brush of the active tool") <sup>[[UI]](#requiresUI "Requires UI")</sup>
* [app.command.ChangeColor](command/ChangeColor.md#changecolor "Changes the current foreground or background color") <sup>[[UI]](#requiresUI "Requires UI")</sup>
* [app.command.ChangePixelFormat](command/ChangePixelFormat.md#changepixelformat) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.Clear
  * Clear the current active document
* app.command.ClearCel
  * Clear the active cel in unlocked layers
* app.command.ClearRecentFiles
  * Clear the recent files list
* app.command.CloseAllFiles <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Close all open files
* app.command.CloseFile <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Close the active file
* [app.command.ColorCurve](command/ColorCurve.md#colorcurve) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.ColorQuantization](command/ColorQuantization.md#colorquantization "Creates a palette from the current sprite") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.ContiguousFill
  * Changes the current tool to Contiguous Fill
* [app.command.ConvolutionMatrix](command/ConvolutionMatrix.md#convolutionmatrix "Select and apply a convolution matrix to the image") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.CopyColors](command/CopyColors.md#copycolors)
* app.command.CopyMerged
  * Copies the active sprite as a merged image to the clipboard
* app.command.Copy
  * Performs a copy command on the current selection
* [app.command.CropSprite](command/CropSprite.md#cropsprite)
* app.command.Cut
  * Performs a cut command on the current selection
* app.command.DeselectMask
   * Deselects the current mask
* [app.command.Despeckle](command/Despeckle.md#despeckle "Applies median blur") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.DeveloperConsole <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the developer console (experimental)
* app.command.DiscardBrush <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Discard the active brush
* app.command.DuplicateLayer
  * Duplicate the currently selected layer
* [app.command.DuplicateSprite](command/DuplicateSprite.md#duplicatesprite) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.DuplicateView <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Duplicates the current workspace view
* app.command.Exit <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Instructs Aseprite to exit, the user will be prompted to save if any files are modified and it can be canceled
* [app.command.ExportSpriteSheet](command/ExportSpriteSheet.md#exportspritesheet) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.ExportTileset](command/ExportTileset.md#exporttileset) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.Eyedropper
  * Grabs the color under the current mouse position with the Eyedropper tool
* app.command.Fill
  * Performs a foreground color fill on the current selection mask
* app.command.FitScreen <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Resets the zoom on the current view to fit the screen
* [app.command.FlattenLayers](command/FlattenLayers.md#flattenlayers)
* [app.command.Flip](command/Flip.md#flip)
* [app.command.FrameProperties](command/FrameProperties.md#frameproperties) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.FrameTagProperties](command/FrameTagProperties.md#frametagproperties) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.FullscreenPreview <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the full screen preview
* app.command.GotoFirstFrameInTag <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoFirstFrame <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoFrame <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoLastFrameInTag <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoLastFrame <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoNextFrameWithSameTag <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoNextFrame <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoNextLayer <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoNextTab <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoPreviousFrameWithSameTag <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoPreviousFrame <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoPreviousLayer <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GotoPreviousTab <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.GridSettings <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the grid settings window
* app.command.Home <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the Home tab
* [app.command.HueSaturation](command/HueSaturation.md#huesaturation) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.ImportSpriteSheet](command/ImportSpriteSheet.md#importspritesheet) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.InvertColor](command/InvertColor.md#invertcolor) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.InvertMask
  * Inverts the current selection mask, or if there is none, selects all
* app.command.KeyboardShortcuts <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the keyboard shortcut menu, use the `search` parameter to pre-fill the searchbar
* app.command.Launch
  * Opens the given `path` in the desktop web browser as relative path to aseprite.org or a full URL
* app.command.LayerFromBackground
  * Converts the active background layer to a regular layer
* app.command.LayerLock
  * Toggles the lock of active layers
* [app.command.LayerOpacity](command/LayerOpacity.md#layeropacity)
* app.command.LayerProperties <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the Layer property window for the active layer
* app.command.LayerVisibility
  * Toggles the visibility of the active layer
* app.command.LinkCels
  * Links the selected cels together
* [app.command.LoadMask](command/LoadMask.md#loadmask "Loads a selection from file") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.LoadPalette](command/LoadPalette.md#loadpalette "Loads a palette from file") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.MaskAll
  * Selects all
* [app.command.MaskByColor](command/MaskByColor.md#maskbycolor "Creates a new selection by color") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.MaskContent
  * Selects the content from the active sprite (like autocrop)
* app.command.MergeDownLayer
  * Merges the active layer down
* [app.command.ModifySelection](command/ModifySelection.md#modifyselection) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.MoveCel <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Finishes the move operation of a cel in the timeline
* [app.command.MoveColors](command/MoveColors.md#movecolors)
* [app.command.MoveMask](command/MoveMask.md#movemask "Moves the selection boundaries or its content (pixels).")
* app.command.NewBrush <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Create a new brush from the current selection/editor
* [app.command.NewFile](command/NewFile.md#newfile)
* app.command.NewFrameTag <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Shows the New Tag dialog for the selected frame range
* [app.command.NewFrame](command/NewFrame.md#newframe)
* [app.command.NewLayer](command/NewLayer.md#newlayer) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.NewSpriteFromSelection
  * Creates a new sprite from the current selection mask
* app.command.OpenBrowser <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Open the given `filename` in the internal text browser
* [app.command.OpenFile](command/OpenFile.md#openfile)
* app.command.OpenGroup
  * Opens the active layer group
* app.command.OpenInFolder
  * Opens the folder of the active sprite in the file explorer
* app.command.OpenScriptFolder
  * Opens the Aseprite script folder in the file explorer
* app.command.OpenWithApp
  * Opens the active sprite with the native app assigned to the format
* [app.command.Options](command/Options.md#options) <sup>[[UI]](#requiresUI "Requires UI")</sup>
* [app.command.Outline](command/Outline.md#outline) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.PaletteEditor <sup>[[UI]](#requiresUI "Requires UI")</sup>
   * Show the palette editor popup
* [app.command.PaletteSize](command/PaletteSize.md#palettesize "Changes the palette size") <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.PasteText <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Opens the Insert Text dialog
* app.command.Paste
  * Pastes the clipboard into the current active sprite/selection, at coordinates `x` and `y` (if given)
* app.command.PixelPerfectMode
  * Toggles the "pixel perfect" freehand algorithm
* app.command.PlayAnimation <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Plays the sprite's animation, if any
* app.command.PlayPreviewAnimation <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Plays the animation in the preview window (enables it if it's not visible)
* app.command.Redo
  * Equivalent to `app.redo()`
* app.command.Refresh <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Refreshes the user interface
* app.command.RemoveFrameTag
  * Remove a tag by the given `name` or object `id`
* app.command.RemoveFrame
  * Remove the selected or the current active frame(s) (only if there's more 1 frame total)
* app.command.RemoveLayer
  * Remove the selected or current active layer(s) (only if there's more than 1 layer total)
* app.command.RemoveSlice
  * Remove a slice by `name` or object `id`
* app.command.RepeatLastExport <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
  * Redoes the last export command
* [app.command.ReplaceColor](command/ReplaceColor.md#replacecolor) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.ReselectMask
  * Re-selects a hidden selection mask
* app.command.ReverseFrames
  * Reverses frames (only if there are 2 or more in the selected range)
* [app.command.Rotate](command/Rotate.md#rotate)
* app.command.RunScript
  * Run a script given by the `filename` parameter - any other parameters are passed to the script.
* [app.command.SaveFile](command/SaveFile.md#savefile) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.SaveFileAs](command/SaveFile.md#savefileas) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.SaveFileCopyAs](command/SaveFile.md#savefile) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.SaveMask](command/SaveMask.md#savemask) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* [app.command.SavePalette](command/SavePalette.md#savepalette) <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
* app.command.ScrollCenter <sup>[[*]](#canHaveUI "Can have UI interaction")</sup>
  * Center the editor viewport
* [app.command.Scroll](command/Scroll.md#scroll) <sup>[[UI]](#requiresUI "Requires UI")</sup>
* app.command.SelectTile <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Select the tile under the mouse, with a selection `mode` ([SelectionMode](selectionmode.md))
* app.command.SelectionAsGrid
  * Set the grid bounds to the current selection mask
* app.command.SetColorSelector <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Changes the color selector to the `type`: `"spectrum"`, `"tint-shade-tone"`, `"rgb-wheel"`, `"ryb-wheel"` or `"normal-map-wheel"`
* [app.command.SetInkType](command/SetInkType.md) <sup>[[UI]](#requiresUI "Requires UI")</sup>
* [app.command.SetLoopSection](command/SetLoopSection.md "Sets the looping property of the given frame range")
* app.command.SetPaletteEntrySize <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Set the palette entry size to the given `size` (defaults to `7`)
* app.command.SetSameInk
  * Set the same ink for all tools
* app.command.ShowAutoGuides
  * Toggles the "Show Auto Guides" preference
* app.command.ShowBrushPreview
  * Toggles the "Brush Preview" preference
* app.command.ShowExtras
  * Toggles the "Show Extras" preference
* app.command.ShowGrid
  * Toggles the "Show Grid" preference
* app.command.ShowLayerEdges
  * Toggles the "Show Layer Edges" preference
* app.command.ShowOnionSkin
  * Toggles the "Onion Skin" preference
* app.command.ShowPixelGrid
  * Toggles the "Show Pixel Grid"  preference
* app.command.ShowSelectionEdges
  * Toggles the "Show Selection Edges" preference
* app.command.ShowSlices
  * Toggles the "Show Slices" preference
* app.command.SliceProperties <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Shows the slice properties window by `name` or `id` parameters, otherwise uses the selected slice(s)
* app.command.SnapToGrid
  * Toggles the snap to grid property
* app.command.SpriteProperties
  * Shows the sprite properties window
* [app.command.SpriteSize](command/SpriteSize.md#spritesize)
* app.command.Stroke
   * Performs a foreground color stroke fill on the current selection mask
* app.command.SwitchColors <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Swaps the current foreground/background colors around
* app.command.SymmetryMode
  * Sets the symmetry mode `orientation` to one of `"vertical"`, `"horizontal"`, `"right_diagonal"` or `"left_diagonal"`. Defaults to none, which turns the mode off
* app.command.TiledMode
  * Sets the tiled to mode `axis` to one of `"both"`, `"x"` or `"y"`. Defaults to none, which turns the mode off
* app.command.Timeline <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Changes the timeline visibility with the parameters `open`, `close` and `switch`
* app.command.TogglePreview <sup>[[UI]](#requiresUI "Requires UI")</sup>
  * Toggles the visibility of the preview window
* app.command.ToggleTimelineThumbnails
  * Toggles the timeline thumbnails preference
* app.command.UndoHistory
  * Shows the undo history window
* app.command.Undo
* app.command.UnlinkCel
  * Equivalent to `app.undo()`
* [app.command.Zoom](command/Zoom.md#zoom "Changes the zoom on the active editor") <sup>[[UI]](#requiresUI "Requires UI")</sup>

## Annotations

<a name="canHaveUI"></a>
> **[*]** - Can have UI interactions, controlled by the `ui` parameter.

<a name="requiresUI"></a>
> **[UI]** - Requires the UI to be present, cannot be used in --batch mode.

## Error Handling

If the command fails to run or is disabled, it will return `false`.
To check if a command is enabled and can be run, you can use `app.command.[COMMAND NAME].enabled` before calling it.

## Source

If you cannot find a specific command, you might like to take a look at the
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
