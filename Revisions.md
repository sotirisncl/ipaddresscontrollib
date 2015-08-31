### [Revision 44](https://code.google.com/p/ipaddresscontrollib/source/detail?r=44) (28-Jun-08) ###

  * Changed base of `IPAddressControl` to `ContainerControl` so that its `AutoScaleMode` could be set to `AutoScaleMode.Dpi`.  Also set the `FixedWidth` and `FixedHeight` control styles to true.  These changes fix rendering problems when screen resolution is 120 dpi.
  * Using `Graphics.DrawString()` rather than `TextRenderer.DrawText()` in `DotControl`.  `TextRenderer` does not use the correct baseline at 120 dpi.
  * Rearranged some `enum` and `EventArgs` so that each control class is the first class in its file.

### [Revision 36](https://code.google.com/p/ipaddresscontrollib/source/detail?r=36) (27-Apr-08) ###

  * Added propagation of `KeyDown`, `KeyUp`, and `PreviewKeyDown` events. `Keys.Enter` and `Keys.Return` will now propagate a `KeyPress` event.


### [Revision 29](https://code.google.com/p/ipaddresscontrollib/source/detail?r=29) (16-Dec-07) ###

  * Added a Visual Studio 2008 project.  The VS 2005 and VS 2008 projects have the same source code.  Some minor changes were made to remove code analysis warnings.

### [Revision 26](https://code.google.com/p/ipaddresscontrollib/source/detail?r=26) (23-Oct-07) ###

  * Fixed an issue with `ReadOnly` controls still being editable.


### [Revision 22](https://code.google.com/p/ipaddresscontrollib/source/detail?r=22) (27-Sep-07) ###

  * Added event propagation for focus, key press, and some mouse events.
  * Added `AllowInternalTab` and `AnyBlank` properties.
  * Removed superfluous code.
  * Removed a potential resource leak when calculating text size and added a `null` check for `SetAddressBytes()`.
  * Compliant with FxCop 1.35.

### [Revision 15](https://code.google.com/p/ipaddresscontrollib/source/detail?r=15) (2-Jul-07) ###

  * Initial release at Google Code.
  * Text set in design mode is persisted.
  * Removed override of `AutoSize`.  Use `AutoHeight` instead.
  * (VS05) Modified size calculations to conserve horizontal space.

### Prior Changes ###

  * 6-Mar-07
    * Now checks for `null` when parsing incoming text.

  * 21-Feb-07
    * Added handling of `Keys.Backspace` across fields.
    * Added better handling of `Keys.Delete`, and new handlers for `Keys.Home` and `Keys.End`.
    * (VS05) Modified the `MinimumSize` property of `DotControl` to tighten up the spacing.

  * 5-May-06
    * (VS05) Added `Baseline` to the `SnapLines` collection for the `ControlDesigner` class. Made `Text` property browsable in design mode. Fixed a control sizing bug when large fonts are used.

  * 13-Oct-05
    * Compliant with FxCop 1.32.

  * 17-Sep-05
    * Enhanced to support Windows XP visual styles.

  * 3-Aug-05
    * Bug fix for `Focused` property.

  * 22-Mar-05
    * Added a call to `OnTextChanged()` for the control when the text of any field changes.

  * 6-Feb-05
    * Added missing key handlers.
    * Added sizing.
    * Added `ReadOnly` property.
    * Non-standard color choices now render properly.
    * Added an event to notify clients of text change.

  * 20-Jan-05
    * Initial release.