---
id: maxgui.maxgui
title: MaxGUI.MaxGUI
sidebar_label: MaxGUI.MaxGUI
---


The MaxGUI module contains commands to create and control user interfaces for developing applications in BlitzMax.

Users should be familiar with the [WaitEvent](../../brl/brl.eventqueue/#function-waitevent-int) command and BlitzMax events which provide the basic communication mechanism 
between user interface and program when developing MaxGUI applications.
<h1>Gadgets</h1>
MaxGUI provides numerous types of gadgets that can be created and arranged for the purposes of providing a user interface to
BlitzMax applications.

The position of gadgets in relation to their group (parent) gadget can be controlled with the [SetGadgetShape](../../maxgui/maxgui.maxgui/#function-setgadgetshape-gadget-tgadget-x-y-w-h) command and 
monitored with the [GadgetX](../../maxgui/maxgui.maxgui/#function-gadgetx-gadget-tgadget), [GadgetY](../../maxgui/maxgui.maxgui/#function-gadgety-gadget-tgadget), [GadgetWidth](../../maxgui/maxgui.maxgui/#function-gadgetwidth-gadget-tgadget) and [GadgetHeight](../../maxgui/maxgui.maxgui/#function-gadgetheight-gadget-tgadget) commands. Gadgets that can act as group gadgets 
(such as Windows, Tabbers and Panels) have an inner client region that contains their children, with an area that can be 
found using [ClientWidth](../../maxgui/maxgui.maxgui/#function-clientwidth-gadget-tgadget) and [ClientHeight](../../maxgui/maxgui.maxgui/#function-clientheight-gadget-tgadget).

Gadgets can be made to automatically reposition themselves when their group gadget changes size with the [SetGadgetLayout](../../maxgui/maxgui.maxgui/#function-setgadgetlayout-gadget-tgadget-left-right-top-bottom)
command.

A gadget's group, or parent, gadget can be retrieved using the [GadgetGroup](../../maxgui/maxgui.maxgui/#function-gadgetgroup-tgadget-gadget-tgadget) command. A gadget can be shown with [ShowGadget](../../maxgui/maxgui.maxgui/#function-showgadget-gadget-tgadget),
hidden with [HideGadget](../../maxgui/maxgui.maxgui/#function-hidegadget-gadget-tgadget), its visibility found with the [GadgetHidden](../../maxgui/maxgui.maxgui/#function-gadgethidden-gadget-tgadget-recursive-false) function and removed completely from the system with
the [FreeGadget](../../maxgui/maxgui.maxgui/#function-freegadget-gadget-tgadget) command. It is now also possible to determine a gadget's class/type using the [GadgetClass](../../maxgui/maxgui.maxgui/#function-gadgetclass-gadget-tgadget) command.

[EnableGadget](../../maxgui/maxgui.maxgui/#function-enablegadget-gadget-tgadget), [DisableGadget](../../maxgui/maxgui.maxgui/#function-disablegadget-gadget-tgadget) and [GadgetDisabled](../../maxgui/maxgui.maxgui/#function-gadgetdisabled-gadget-tgadget-recursive-false) control and determine if a gadget is currently enabled.

[ActivateGadget](../../maxgui/maxgui.maxgui/#function-activategadget-gadget-tgadget) will set a particular gadget as active so that it is highlighted and receives any keyboard events while
[ActiveGadget](../../maxgui/maxgui.maxgui/#function-activegadget-tgadget) returns which gadget (if any) is currently active.

[SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), [SetGadgetFont](../../maxgui/maxgui.maxgui/#function-setgadgetfont-gadget-tgadget-font-tguifont-applytochildren-int-false), [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true) and [SetGadgetTextColor](../../maxgui/maxgui.maxgui/#function-setgadgettextcolor-gadget-tgadget-r-g-b) change the appearance of many of the MaxGUI gadgets.

Those wanting to store their own object with gadget can do so using the [SetGadgetExtra](../../maxgui/maxgui.maxgui/#function-setgadgetextra-gadget-tgadget-extra-object) command - a reference to your object
will be stored inside the <b>TGadget</b> type and is retrievable using the matching [GadgetExtra](../../maxgui/maxgui.maxgui/#function-gadgetextra-object-gadget-tgadget) command. The object reference will
be overwritten by future calls to [SetGadgetExtra](../../maxgui/maxgui.maxgui/#function-setgadgetextra-gadget-tgadget-extra-object) or when [FreeGadget](../../maxgui/maxgui.maxgui/#function-freegadget-gadget-tgadget) is called.

Recently, [SetGadgetTooltip](../../maxgui/maxgui.maxgui/#function-setgadgettooltip-gadget-tgadget-tip) and [GadgetTooltip](../../maxgui/maxgui.maxgui/#function-gadgettooltip-gadget-tgadget) have been added to MaxGUI to allow tooltips to be set on standard
<i>non list-based</i> gadgets, including Buttons, Labels, TextFields etc.

Tooltips are set on an item-by-item basis for gadgets such as ListBoxes and Tabbers etc. 
Attempting to set an overall gadget tooltip on a <i>list-based</i> gadget will have no effect.

Finally, a more generic [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon) command has been added which will eventually allow you to set pixmaps for many 
gadgets (not just for panels), depending on your platform. 

<h2>Events</h2>
Gadgets that allow user-interaction emit events that can be caught and processed in your main application
loop (typically with the [WaitEvent](../../brl/brl.eventqueue/#function-waitevent-int) command). The events a gadget can generate will be listed under the
corresponding CreateGadget() documentation.

It is important to note, however, that events are only emitted when <b>the user</b> interacts with, or changes the
state, of a gadget. Any changes made to gadget through MaxGUI command calls (such as [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index)) should 
not result in events being emitted. 

<h2>Windows</h2>
![](assets/win32window.png)![](assets/fltkwindow.png)![](assets/osxwindow.png)

A Window is used to contain a collection of gadgets that make up the user interface of an application. The [CreateWindow](../../maxgui/maxgui.maxgui/#function-createwindow-tgadget-titletext-x-y-w-h-group-tgadget-null-style-window-default) 
command creates a window of a specified size that can then be used as the <b>group</b> parameter for the other gadget creation
commands.

The [WindowMenu](../../maxgui/maxgui.maxgui/#function-windowmenu-tgadget-window-tgadget) command returns a handle that can be used as the parent parameter of the [CreateMenu](../../maxgui/maxgui.maxgui/#function-createmenu-tgadget-text-tag-parent-tgadget-hotkey-0-modifier-0) command to add menus
to a window. [UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget) should be called after adding/changing a window's menu for the changes to take effect.
A window can be activated (bringing the window in front, with focus) with the [ActivateWindow](../../maxgui/maxgui.maxgui/#function-activatewindow-window-tgadget) command. 
The text displayed in a window's optional status-bar can be set using the [SetStatusText](../../maxgui/maxgui.maxgui/#function-setstatustext-window-tgadget-text) command.

If a window is created with the WINDOW_RESIZABLE style, its sizing can be restrained using [SetMinWindowSize](../../maxgui/maxgui.maxgui/#function-setminwindowsize-window-tgadget-w-h) and 
[SetMaxWindowSize](../../maxgui/maxgui.maxgui/#function-setmaxwindowsize-window-tgadget-w-h) and it can be minimized, maximized and restored with the [MinimizeWindow](../../maxgui/maxgui.maxgui/#function-minimizewindow-window-tgadget), [MaximizeWindow](../../maxgui/maxgui.maxgui/#function-maximizewindow-window-tgadget) and 
[RestoreWindow](../../maxgui/maxgui.maxgui/#function-restorewindow-window-tgadget) commands. The state of a window can be dermined using [WindowMinimized](../../maxgui/maxgui.maxgui/#function-windowminimized-window-tgadget) and [WindowMaximized](../../maxgui/maxgui.maxgui/#function-windowmaximized-window-tgadget).

<h2>Menus</h2>
![](assets/win32menu.png)![](assets/fltkmenu.png)![](assets/osxmenu.png)

The [CreateMenu](../../maxgui/maxgui.maxgui/#function-createmenu-tgadget-text-tag-parent-tgadget-hotkey-0-modifier-0) command is used to create menu-items. Menus can be attached either to a window's menu-bar by parenting them to a 
[WindowMenu](../../maxgui/maxgui.maxgui/#function-windowmenu-tgadget-window-tgadget) or can popup at the current mouse location if used with the [PopupWindowMenu](../../maxgui/maxgui.maxgui/#function-popupwindowmenu-window-tgadget-menu-tgadget-extra-object-null) command.

[CheckMenu](../../maxgui/maxgui.maxgui/#function-checkmenu-menu-tgadget) adds a tick next to a menu-item and [UncheckMenu](../../maxgui/maxgui.maxgui/#function-uncheckmenu-menu-tgadget) removes it.  [DisableGadget](../../maxgui/maxgui.maxgui/#function-disablegadget-gadget-tgadget) will "gray out" a menu item, preventing it from
being chosen by the user. [EnableGadget](../../maxgui/maxgui.maxgui/#function-enablegadget-gadget-tgadget) reverses this operation.

<h2>Buttons</h2>
![](assets/win32buttons.png)![](assets/fltkbuttons.png)![](assets/osxbuttons.png)

The [CreateButton](../../maxgui/maxgui.maxgui/#function-createbutton-tgadget-label-x-y-w-h-group-tgadget-style-button-push) command is used to add buttons to a group gadget. Buttons can be standard push buttons that emit a single
event whenever clicked, or they can be created with the BUTTON_CHECKBOX or BUTTON_RADIO styles
in which case they can be toggled by the user (or programatically with the [SetButtonState](../../maxgui/maxgui.maxgui/#function-setbuttonstate-button-tgadget-checked) command). 
Their current state can be found with the help of the [ButtonState](../../maxgui/maxgui.maxgui/#function-buttonstate-button-tgadget) function.

<h2>Panels</h2>
![](assets/win32panels.png)![](assets/fltkpanels.png)![](assets/osxpanels.png)

The [CreatePanel](../../maxgui/maxgui.maxgui/#function-createpanel-tgadget-x-y-w-h-group-tgadget-style-0-title) command is used to to create a Panel gadget. Panels can be used to group other gadgets together and
can be optionally assigned a background color or image using the [SetPanelColor](../../maxgui/maxgui.maxgui/#function-setpanelcolor-panel-tgadget-r-g-b) or [SetPanelPixmap](../../maxgui/maxgui.maxgui/#function-setpanelpixmap-panel-tgadget-pixmap-tpixmap-flags-panelpixmap-tile) commands.  They can
be created with or without a border. Panels were one of the first gadgets that could emit mouse/key events by 
specifying the optional PANEL_ACTIVE style upon creation.

<h2>Text Fields</h2>
![](assets/win32textfield.png)![](assets/fltktextfield.png)![](assets/osxtextfield.png)

A text-field allows the users to enter a single line of text. A text-field's characters can be masked by specifying an 
optional TEXTFIELD_PASSWORD style flag upon the call to [CreateTextField](../../maxgui/maxgui.maxgui/#function-createtextfield-tgadget-x-y-w-h-group-tgadget-style-0).  This is useful for creating password-entry
forms.  As with all other gadgets, [GadgetText](../../maxgui/maxgui.maxgui/#function-gadgettext-gadget-tgadget) and [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text) can be used to set and retrieve the text in the field.

<h2>Text Areas</h2>
![](assets/win32textarea.png)![](assets/fltktextarea.png)![](assets/osxtextarea.png)

The [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0) command creates a gadget for displaying formatted text, with optional TEXTAREA_WORDWRAP and 
TEXTAREA_READONLY styles.  

The MaxGUI commands specific to text-areas are summarised below:
 
* [SetTextAreaText](../../maxgui/maxgui.maxgui/#function-settextareatext-textarea-tgadget-text-pos-0-length-textarea-all-units-textarea-chars) and [AddTextAreaText](../../maxgui/maxgui.maxgui/#function-addtextareatext-textarea-tgadget-text) allow for convenient editing of the text.
* [TextAreaText](../../maxgui/maxgui.maxgui/#function-textareatext-textarea-tgadget-pos-0-length-textarea-all-units-textarea-chars) returns either a specified portion or the entire contents of a text-area.
* [TextAreaLen](../../maxgui/maxgui.maxgui/#function-textarealen-textarea-tgadget-units-textarea-chars) returns the number of characters or lines currently contained.
* [TextAreaCursor](../../maxgui/maxgui.maxgui/#function-textareacursor-textarea-tgadget-units-textarea-chars) and [TextAreaSelLen](../../maxgui/maxgui.maxgui/#function-textareasellen-textarea-tgadget-units-textarea-chars) commands return the cursor position and selection length.
* [SelectTextAreaText](../../maxgui/maxgui.maxgui/#function-selecttextareatext-textarea-tgadget-pos-0-length-textarea-all-units-textarea-chars) command provides a means to programatically select/highlight text.
* [SetTextAreaFont](../../maxgui/maxgui.maxgui/#function-settextareafont-textarea-tgadget-font-tguifont) and [SetTextAreaColor](../../maxgui/maxgui.maxgui/#function-settextareacolor-textarea-tgadget-r-g-b-bg-false) affect the style and appearance of the text displayed in a Text Area. 
* [SetTextAreaTabs](../../maxgui/maxgui.maxgui/#function-settextareatabs-textarea-tgadget-tabwidth) allows you to alter the position of tab stops.
* [FormatTextAreaText](../../maxgui/maxgui.maxgui/#function-formattextareatext-textarea-tgadget-r-g-b-flags-pos-0-length-textarea-all-units-textarea-chars) allows sections of text to be formatted using their own colors and font styles. 
* [LockTextArea](../../maxgui/maxgui.maxgui/#function-locktextarea-textarea-tgadget) and [UnlockTextArea](../../maxgui/maxgui.maxgui/#function-unlocktextarea-textarea-tgadget) commands should be used to improve performance when formatting lots of text.
* [TextAreaChar](../../maxgui/maxgui.maxgui/#function-textareachar-textarea-tgadget-line) and [TextAreaLine](../../maxgui/maxgui.maxgui/#function-textarealine-textarea-tgadget-index) commands convert between line and character positions.
* [TextAreaCharX](../../maxgui/maxgui.maxgui/#function-textareacharx-textarea-tgadget-char) and [TextAreaCharY](../../maxgui/maxgui.maxgui/#function-textareachary-textarea-tgadget-char) find the x,y coordinates of a character position relative to the top-left corner
of the gadget.

<h2>Combo Boxes</h2>
![](assets/win32combobox.png)![](assets/fltkcombobox.png)![](assets/osxcombobox.png)

Combo-boxes provide a dropdown list of options to the user with an optional style that allows the user to enter 
their own text in a similar manner to the TextField gadget. [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0) creates a ComboBox and the standard
list based gadget commands [ClearGadgetItems](../../maxgui/maxgui.maxgui/#function-cleargadgetitems-gadget-tgadget), [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null), [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [RemoveGadgetItem](../../maxgui/maxgui.maxgui/#function-removegadgetitem-gadget-tgadget-index), [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index),
[SelectedGadgetItem](../../maxgui/maxgui.maxgui/#function-selectedgadgetitem-gadget-tgadget), [CountGadgetItems](../../maxgui/maxgui.maxgui/#function-countgadgetitems-gadget-tgadget) and [GadgetItemText](../../maxgui/maxgui.maxgui/#function-gadgetitemtext-gadget-tgadget-index) can be used to manage the items contained by the ComboBox gadget.

<h2>List Boxes</h2>
![](assets/win32listbox.png)![](assets/fltklistbox.png)![](assets/osxlistbox.png)

List-boxes are similiar to ComboBoxes but features a scrolling list rather than a drop-down selection mechanism.
The [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0) command is used to create a ListBox gadget while the standard list based gadget commands listed
in the previous ComboBox section are used to manage the items.

<h2>Toolbars</h2>
![](assets/win32toolbar.png)

Toolbars display a row of clickable icons at the top of a window. The [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) command creates a window toolbar 
using a previously loaded <b>TIconStrip</b> or using a specified image file containing a strip of icons.

[EnableGadgetItem](../../maxgui/maxgui.maxgui/#function-enablegadgetitem-gadget-tgadget-index) and [DisableGadgetItem](../../maxgui/maxgui.maxgui/#function-disablegadgetitem-gadget-tgadget-index) control the interactive state of individual items while [SetToolbarTips](../../maxgui/maxgui.maxgui/#function-settoolbartips-toolbar-tgadget-tips)
assigns a list of meaningful strings to the toolbar items.

The recommended icon size for toolbars is 24x24 pixels which seems to work well on most platforms. Using a different
image size may result in the pixmaps being scaled before being set depending on the OS.

It is important to note that Toolbars should only ever be added to <b>Window</b>s - adding ToolBars to other group gadgets may
cause your program to crash on some platforms.

<h2>Tabbers</h2>
![](assets/win32tabber.png)![](assets/fltktabber.png)![](assets/osxtabber.png)

The [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0) command creates a tab control gadget commonly used to group gadgets into a collection of pages. 
The standard list based gadget commands [ClearGadgetItems](../../maxgui/maxgui.maxgui/#function-cleargadgetitems-gadget-tgadget), [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null), [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [RemoveGadgetItem](../../maxgui/maxgui.maxgui/#function-removegadgetitem-gadget-tgadget-index), 
[SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index), [SelectedGadgetItem](../../maxgui/maxgui.maxgui/#function-selectedgadgetitem-gadget-tgadget), [CountGadgetItems](../../maxgui/maxgui.maxgui/#function-countgadgetitems-gadget-tgadget) and [GadgetItemText](../../maxgui/maxgui.maxgui/#function-gadgetitemtext-gadget-tgadget-index) can be used to manage the items contained 
in a Tabber gadget.

<h2>TreeViews</h2>
![](assets/win32treeview.png)![](assets/fltktreeview.png)![](assets/osxtreeview.png)

A TreeView is used to display hierarchical data where items are contained in nodes that can be children of other nodes.
The [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0) command creates a new TreeView gadget that provides a [TreeViewRoot](../../maxgui/maxgui.maxgui/#function-treeviewroot-tgadget-treeview-tgadget) used to create a tree of nodes.

[AddTreeViewNode](../../maxgui/maxgui.maxgui/#function-addtreeviewnode-tgadget-text-node-tgadget-icon-1-extra-object-null), [InsertTreeViewNode](../../maxgui/maxgui.maxgui/#function-inserttreeviewnode-tgadget-index-text-node-tgadget-icon-1-extra-object-null), [ModifyTreeViewNode](../../maxgui/maxgui.maxgui/#function-modifytreeviewnode-node-tgadget-text-icon-1), [ExpandTreeViewNode](../../maxgui/maxgui.maxgui/#function-expandtreeviewnode-node-tgadget), [CollapseTreeViewNode](../../maxgui/maxgui.maxgui/#function-collapsetreeviewnode-node-tgadget) and
[FreeTreeViewNode](../../maxgui/maxgui.maxgui/#function-freetreeviewnode-node-tgadget) provide commands to control the the contents of a TreeView.

[SelectedTreeViewNode](../../maxgui/maxgui.maxgui/#function-selectedtreeviewnode-tgadget-treeview-tgadget) and [SelectTreeViewNode](../../maxgui/maxgui.maxgui/#function-selecttreeviewnode-node-tgadget) return and set the currently highlighted node in a TreeView while 
[CountTreeViewNodes](../../maxgui/maxgui.maxgui/#function-counttreeviewnodes-node-tgadget) returns the number  of nodes contained in a single TreeViewNode. [FreeTreeViewNode](../../maxgui/maxgui.maxgui/#function-freetreeviewnode-node-tgadget) and [ClearTreeView](../../maxgui/maxgui.maxgui/#function-cleartreeview-treeview-tgadget)
can be used to remove nodes previously added to a TreeView gadget.

<h2>HtmlViews</h2>
![](assets/win32htmlview.png)

An HTMLView is a gadget containing a complete web browser display. The [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0) command creates an HTMLView gadget
while [HtmlViewGo](../../maxgui/maxgui.maxgui/#function-htmlviewgo-view-tgadget-url), [HtmlViewBack](../../maxgui/maxgui.maxgui/#function-htmlviewback-view-tgadget) and [HtmlViewForward](../../maxgui/maxgui.maxgui/#function-htmlviewforward-view-tgadget) control the page being displayed.

[HtmlViewStatus](../../maxgui/maxgui.maxgui/#function-htmlviewstatus-view-tgadget) and [HtmlViewCurrentURL](../../maxgui/maxgui.maxgui/#function-htmlviewcurrenturl-view-tgadget) provide extended information about the state of an HTMLView gadget while
[HtmlViewRun](../../maxgui/maxgui.maxgui/#function-htmlviewrun-view-tgadget-script) allows scripts (i.e. javascript) to be run (on some platforms).

<h2>Labels</h2>
Labels are read-only regions of text on a user inteface that do not have a background and are created with the 
[CreateLabel](../../maxgui/maxgui.maxgui/#function-createlabel-tgadget-name-x-y-w-h-group-tgadget-style-label-left) command.

<h2>Sliders</h2>
![](assets/win32sliders.png)![](assets/fltksliders.png)![](assets/osxsliders.png)

Sliders allow the user to control a numerical value by dragging a control inside a container. [CreateSlider](../../maxgui/maxgui.maxgui/#function-createslider-tgadget-x-y-w-h-group-tgadget-style-0) can create 
both a scroll-bar type slider (where the size of the knob represents the portion of the document being viewed) and 
trackbar style sliders (where the knob is a fixed size and [SetSliderRange](../../maxgui/maxgui.maxgui/#function-setsliderrange-slider-tgadget-range0-range1) controls the minimum and maximum values 
allowed by the control).

[SetSliderValue](../../maxgui/maxgui.maxgui/#function-setslidervalue-slider-tgadget-value) and [SliderValue](../../maxgui/maxgui.maxgui/#function-slidervalue-slider-tgadget) set and retrieve the position of a Slider control.

<h2>Progress Bars</h2>
![](assets/win32progbar.png)![](assets/fltkprogbar.png)![](assets/osxprogbar.png)

[CreateProgBar](../../maxgui/maxgui.maxgui/#function-createprogbar-tgadget-x-y-w-h-group-tgadget-style-0) creates a progress bar gadget commonly used to display the progress of an operation. The 
[UpdateProgBar](../../maxgui/maxgui.maxgui/#function-updateprogbar-progbar-tgadget-value) command is used to update the progress bar with a floating point value between 0.0 and 1.0 and
are typically used to represent how complete the current operation is.

<h2>Desktop</h2>
A gadget representing the user's desktop is returned by the [Desktop](../../maxgui/maxgui.maxgui/#function-desktop-tgadget) command. The Desktop gadget is particularly useful
for finding primary screen and workspace resolutions using [GadgetWidth](../../maxgui/maxgui.maxgui/#function-gadgetwidth-gadget-tgadget) / [GadgetHeight](../../maxgui/maxgui.maxgui/#function-gadgetheight-gadget-tgadget) or [ClientWidth](../../maxgui/maxgui.maxgui/#function-clientwidth-gadget-tgadget) / [ClientHeight](../../maxgui/maxgui.maxgui/#function-clientheight-gadget-tgadget) respectively.

The [LookupGuiFont](../../maxgui/maxgui.maxgui/#function-lookupguifont-tguifont-pfonttype-guifont-system-pfontsize-double-0-pfontstyle-0) and [LookupGuiColor](../../maxgui/maxgui.maxgui/#function-lookupguicolor-colorindex-red-byte-var-green-byte-var-blue-byte-var) commands can be used to retrieve system defined font and color information.


## Functions

### `Function SetHotKeyEvent:THotKey( key,mods,event:TEvent=Null,owner:Byte Ptr=0 )`

Set a hotkey event.


When the specified hotkey combination is selected by the user, the specified
<b>event</b> will be emitted using [EmitEvent](../../brl/brl.event/#function-emitevent-event-tevent).

If <b>event</b> is [Null](../../brl/brl.blitz/#null), an event with an <b>id</b> equal to EVENT_HOTKEYHIT, <b>data</b> equal
to <b>key</b> and <b>mods</b> equal to <b>mods</b> will be emitted.

[SetHotKeyEvent](../../maxgui/maxgui.maxgui/#function-sethotkeyevent-thotkey-key-mods-event-tevent-null-owner-byte-ptr-0) will overwrite any existing hotkey event with the same <b>key</b>, <b>mods</b> and <b>owner</b>.

Please refer to the Key Codes module for valid key and modifier codes.


<br/>

### `Function RemoveHotKey(hotkey:THotKey)`

Remove a hotkey event.


Clears a hotkey object created with [SetHotKeyEvent](../../maxgui/maxgui.maxgui/#function-sethotkeyevent-thotkey-key-mods-event-tevent-null-owner-byte-ptr-0).


<br/>

### `Function LookupGuiColor( colorindex, red:Byte Var, green:Byte Var, blue:Byte Var )`

Look-up a system defined color.


<b>colorindex</b> can be one of the following values:

<table><tr><td> <b>Constant</b></td><td><b>Description</b></td><td><b>Fall Back</b></td></tr><tr><td>  GUICOLOR_WINDOWBG</td><td>Window/panel background color.</td><td>R: 240, G: 240, B: 240</td></tr><tr><td>  GUICOLOR_GADGETBG</td><td>Gadget background color (e.g. textfield).</td><td>R: 255, G: 255, B: 255</td></tr><tr><td>  GUICOLOR_GADGETFG</td><td>Gadget text color.</td><td>R: 0, G: 0, B: 0</td></tr><tr><td>  GUICOLOR_SELECTIONBG</td><td>Text selection background color.</td><td>R: 50, G: 150, B: 255</td></tr><tr><td>  GUICOLOR_LINKFG</td><td>Hyperlink text color.</td><td>R: 0, G: 0, B: 255</table>


See Also: [LookupGuiFont](../../maxgui/maxgui.maxgui/#function-lookupguifont-tguifont-pfonttype-guifont-system-pfontsize-double-0-pfontstyle-0), [RequestColor](../../maxgui/maxgui.maxgui/#function-requestcolor-r-g-b)


#### Returns
[True](../../brl/brl.blitz/#true) if a matching color is retrieved from the system, [False](../../brl/brl.blitz/#false) if the hard-coded fall-back is used.


#### Example
```blitzmax
' lookupguicolor.bmx

Strict

Import MaxGUI.Drivers

AppTitle = "LookupGuiColor() Example"

Global wndMain:TGadget = CreateWindow( AppTitle, 100, 100, 300, 200, Null, WINDOW_TITLEBAR|WINDOW_STATUS )

	Global pnlMain:TGadget = CreatePanel( 0, 0, ClientWidth(wndMain), ClientHeight(wndMain), wndMain )
	
		Global cmbColors:TGadget = CreateComboBox( 5, 5, ClientWidth(wndMain) - 10, 28, pnlMain )
		
		' Populate combo-box with the available color constants
		
		AddGadgetItem cmbColors, "GUICOLOR_WINDOWBG", GADGETITEM_DEFAULT, GUICOLOR_WINDOWBG
		AddGadgetItem cmbColors, "GUICOLOR_GADGETBG", 0, GUICOLOR_GADGETBG
		AddGadgetItem cmbColors, "GUICOLOR_GADGETFG", 0, GUICOLOR_GADGETFG
		AddGadgetItem cmbColors, "GUICOLOR_SELECTIONBG", 0, GUICOLOR_SELECTIONBG
		AddGadgetItem cmbColors, "GUICOLOR_LINKFG", 0, GUICOLOR_LINKFG

ActivateGadget cmbColors

Repeat
	Select WaitEvent()
		
		Case EVENT_APPTERMINATE, EVENT_WINDOWCLOSE
			End
			
		Case EVENT_GADGETACTION
			Local red:Byte, green:Byte, blue:Byte
			LookupGuiColor( GadgetItemIcon( cmbColors, EventData() ), red, green, blue )
			SetGadgetColor( pnlMain, red, green, blue )
			SetStatusText( wndMain, "RGB( " + red + ", " + green + ", " + blue + " )" )
			
	EndSelect
Forever
```
<br/>

### `Function RequestColor(r,g,b)`

Prompts the user for a color.


The parameters <b>red</b>, <b>green</b>, <b>blue</b> are the initial color to display in the requester,
with components in the range 0 to 255.

After a color is selected, use the [RequestedRed](../../maxgui/maxgui.maxgui/#function-requestedred), [RequestedGreen](../../maxgui/maxgui.maxgui/#function-requestedgreen) and [RequestedBlue](../../maxgui/maxgui.maxgui/#function-requestedblue)
functions to determine the color chosen by the user.

See Also: [LookupGuiColor](../../maxgui/maxgui.maxgui/#function-lookupguicolor-colorindex-red-byte-var-green-byte-var-blue-byte-var)


#### Returns
[True](../../brl/brl.blitz/#true) if a color is selected, [False](../../brl/brl.blitz/#false) if the requester was cancelled.


#### Example
```blitzmax
' requestcolor.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Local panel:TGadget
Local red,green,blue

window=CreateWindow("RequestColor",40,40,320,240)
panel=CreatePanel(20,20,32,32,window,PANEL_ACTIVE|PANEL_SUNKEN)

While True
	WaitEvent 
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
		Case EVENT_MOUSEDOWN
			If RequestColor(red,green,blue)
				red=RequestedRed()
				green=RequestedGreen()
				blue=RequestedBlue()
				SetPanelColor panel,red,green,blue
			EndIf				
	End Select
Wend
```
<br/>

### `Function RequestedRed()`

Get the red component of the color previously chosen by the user.

See [RequestColor](../../maxgui/maxgui.maxgui/#function-requestcolor-r-g-b) for more information.


<br/>

### `Function RequestedGreen()`

Get the green component of the color previously chosen by the user.

See [RequestColor](../../maxgui/maxgui.maxgui/#function-requestcolor-r-g-b) for more information.


<br/>

### `Function RequestedBlue()`

Get the blue component of the color previously chosen by the user.

See [RequestColor](../../maxgui/maxgui.maxgui/#function-requestcolor-r-g-b) for more information.


<br/>

### `Function RequestFont:TGuiFont(font:TGuiFont=Null)`

Prompts the user to select a system font.


Prompts the user for a font and returns an object that can then be used with the [SetGadgetFont](../../maxgui/maxgui.maxgui/#function-setgadgetfont-gadget-tgadget-font-tguifont-applytochildren-int-false) command.

See Also: [LoadGuiFont](../../maxgui/maxgui.maxgui/#function-loadguifont-tguifont-name-height-double-bold-false-italic-false-underline-false-strikethrough-false), [LookupGuiFont](../../maxgui/maxgui.maxgui/#function-lookupguifont-tguifont-pfonttype-guifont-system-pfontsize-double-0-pfontstyle-0), [FontName](../../maxgui/maxgui.maxgui/#function-fontname-font-tguifont), [FontSize](../../maxgui/maxgui.maxgui/#function-fontsize-double-font-tguifont) and [FontStyle](../../maxgui/maxgui.maxgui/#function-fontstyle-font-tguifont)


#### Returns
A <b>TGuiFont</b> object, or [Null](../../brl/brl.blitz/#null) if no font was selected.


#### Example
```blitzmax
' requestfont.bmx

Import MaxGui.Drivers

Strict 

AppTitle = "RequestFont() Example"

Const teststring:String = "The quick brown fox jumps over the lazy dog."

Local window:TGadget = CreateWindow(AppTitle,50,50,300,200,Null,WINDOW_TITLEBAR|WINDOW_STATUS|WINDOW_RESIZABLE)
	SetMinWindowSize window, GadgetWidth(window), GadgetHeight(window)
	
	Local label:TGadget = CreateLabel(teststring,0,0,ClientWidth(window),ClientHeight(window)-26,window)
		SetGadgetLayout label, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_CENTERED
	
	Local button:TGadget = CreateButton("Select Font",0,ClientHeight(window)-26,ClientWidth(window),26,window)
		SetGadgetLayout button, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_CENTERED, EDGE_ALIGNED

Local font:TGUIFont

Repeat
	Select WaitEvent()
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE
			End
		Case EVENT_GADGETACTION
			font = RequestFont(font)
			If font Then
				SetGadgetFont label, font
				SetStatusText window,FontName(font) + ": " + Int(FontSize(font)+0.5) + "pt"
			EndIf
	End Select
Forever
```
<br/>

### `Function LoadGuiFont:TGuiFont(name$,height:Double,bold=False,italic=False,underline=False,strikethrough=False)`

Load a system font by name.


Loads a system font by name and returns an object that can then be used with the [SetGadgetFont](../../maxgui/maxgui.maxgui/#function-setgadgetfont-gadget-tgadget-font-tguifont-applytochildren-int-false) command.

Depending on the platform, some gadgets may not respond to all or any of the attributes specified in the function
parameters.

See Also: [RequestFont](../../maxgui/maxgui.maxgui/#function-requestfont-tguifont-font-tguifont-null), [LookupGuiFont](../../maxgui/maxgui.maxgui/#function-lookupguifont-tguifont-pfonttype-guifont-system-pfontsize-double-0-pfontstyle-0), [FontName](../../maxgui/maxgui.maxgui/#function-fontname-font-tguifont), [FontSize](../../maxgui/maxgui.maxgui/#function-fontsize-double-font-tguifont) and [FontStyle](../../maxgui/maxgui.maxgui/#function-fontstyle-font-tguifont)


#### Returns
A <b>TGuiFont</b> object, or [Null](../../brl/brl.blitz/#null) if a suitable matching font was not found on the system.


<br/>

### `Function LookupGuiFont:TGuiFont( pFontType% = GUIFONT_SYSTEM, pFontSize:Double = 0, pFontStyle% = 0 )`

Loads a suitable GUI font that best matches the supplied font characteristics.

If the current MaxGUI driver doesn't return a suitable GUI font, then
a hard-coded fall-back font is returned instead, depending upon the platform.

<b>pFontType</b> can take one of the following constants:

<table><tr><td> <b>Constant</b></td><td><b>Windows Fall-Back</b></td><td><b>Mac OS X Fall-Back</b></td><td><b>Linux Fall-Back</b></td><td><b>Description</b></td></tr><tr><td>  GUIFONT_SYSTEM</td><td>MS Shell Dlg</td><td>Lucida Grande</td><td>FreeSerif</td><td>Default font used to draw gadgets by the OS.</td></tr><tr><td>  GUIFONT_SERIF</td><td>Times New Roman</td><td>Times New Roman</td><td>FreeSerif</td><td>Serif font.</td></tr><tr><td>  GUIFONT_SANSSERIF</td><td>Arial</td><td>Helvetica</td><td>FreeSans</td><td>Sans Serif font.</td></tr><tr><td>  GUIFONT_SCRIPT</td><td>Comic Sans MS</td><td>Comic Sans MS</td><td>TSCu_Comic</td><td>Handwriting style font.</td></tr><tr><td>  GUIFONT_MONOSPACED</td><td>Consolas/Courier New</td><td>Courier</td><td>Courier</td><td>Fixed width font typically used for coding.</table>


<b>pFontSize</b> specifies the point size the font should be loaded with. If this value is less than or equal to 0, then
a suitable size is automatically chosen, or a hard-coded alternative is used (usually between 8-13pt).

<b>pFontStyle</b> should specify any additional font styles that the font should be loaded with. A combination of any of the
following flags can be used:

<table><tr><td> <b>Constant</b></td><td><b>Font Style</b></td></tr><tr><td>  FONT_BOLD</td><td>Bold</td></tr><tr><td>  FONT_ITALIC</td><td>Italic</td></tr><tr><td>  FONT_UNDERLINE</td><td>Underlined</td></tr><tr><td>  FONT_STRIKETHROUGH</td><td>*Strikethrough</table>


<i>Note: FONT_STRIKETHROUGH isn't fully supported by all gadgets/platforms.</i>

See Also: [LookupGuiColor](../../maxgui/maxgui.maxgui/#function-lookupguicolor-colorindex-red-byte-var-green-byte-var-blue-byte-var), [RequestFont](../../maxgui/maxgui.maxgui/#function-requestfont-tguifont-font-tguifont-null), [FontName](../../maxgui/maxgui.maxgui/#function-fontname-font-tguifont), [FontSize](../../maxgui/maxgui.maxgui/#function-fontsize-double-font-tguifont) and [FontStyle](../../maxgui/maxgui.maxgui/#function-fontstyle-font-tguifont)


#### Returns
A new <b>TGuiFont</b> instance chosen using the supplied parameters.


#### Example
```blitzmax
' lookupguifont.bmx

Strict

Import MaxGUI.Drivers

AppTitle = "LookupGuiFont() Example"

Const strSampleText$ = "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Nulla eget mauris quis dolor "+..
"ullamcorper dapibus. Duis facilisis ullamcorper metus. Pellentesque eget enim. Vivamus auctor hendrerit turpis. " + ..
"Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Vivamus tincidunt leo quis urna." 

Const intWindowFlags% = WINDOW_TITLEBAR|WINDOW_RESIZABLE|WINDOW_STATUS|WINDOW_CLIENTCOORDS

Global wndMain:TGadget = CreateWindow( AppTitle, 100, 100, 500, 300, Null, intWindowFlags )
	SetMinWindowSize( wndMain, ClientWidth(wndMain), ClientHeight(wndMain) )
Global lstFontTypes:TGadget = CreateListBox(0,0,200,ClientHeight(wndMain),wndMain)
	SetGadgetLayout lstFontTypes,EDGE_ALIGNED,EDGE_CENTERED,EDGE_ALIGNED,EDGE_ALIGNED
	AddGadgetItem lstFontTypes, "GUIFONT_SYSTEM", GADGETITEM_DEFAULT, -1, "Default OS font.", LookupGuiFont(GUIFONT_SYSTEM)
	AddGadgetItem lstFontTypes, "GUIFONT_SERIF", 0, -1, "Serif font.", LookupGuiFont(GUIFONT_SERIF)
	AddGadgetItem lstFontTypes, "GUIFONT_SANSSERIF", 0, -1, "Sans serif font.", LookupGuiFont(GUIFONT_SANSSERIF)
	AddGadgetItem lstFontTypes, "GUIFONT_SCRIPT", 0, -1, "Script/handwriting font.", LookupGuiFont(GUIFONT_SCRIPT)
	AddGadgetItem lstFontTypes, "GUIFONT_MONOSPACED", 0, -1, "Fixed width/coding font.", LookupGuiFont(GUIFONT_MONOSPACED)

Global txtPreview:TGadget = CreateTextArea(200,0,300,ClientHeight(wndMain),wndMain,TEXTAREA_WORDWRAP|TEXTAREA_READONLY)
	SetGadgetLayout txtPreview,EDGE_ALIGNED,EDGE_ALIGNED,EDGE_ALIGNED,EDGE_ALIGNED
	SetTextAreaText( txtPreview, strSampleText )

Global strFontString$

ChooseFont( LookupGuiFont() )

Repeat
	Select WaitEvent()
		Case EVENT_APPTERMINATE, EVENT_WINDOWCLOSE;End
		Case EVENT_GADGETACTION, EVENT_GADGETSELECT
			Select EventSource()
				Case lstFontTypes
					If EventData() >= 0 Then
						ChooseFont( TGuiFont(GadgetItemExtra( lstFontTypes, EventData() )) )
					EndIf
			EndSelect
	EndSelect
	SetStatusText( wndMain, strFontString + "tt" + CurrentEvent.ToString() + "   " )
Forever

Function ChooseFont( pFont:TGuiFont )
	SetGadgetFont( txtPreview, pFont )
	strFontString$ = FontName(pFont) + ", " + Int(FontSize(pFont)) + "pt"
EndFunction
```
<br/>

### `Function FontName$(font:TGuiFont)`

Retrieves the corresponding property from the <b>TGuiFont</b> type instance.

See Also: [LoadGuiFont](../../maxgui/maxgui.maxgui/#function-loadguifont-tguifont-name-height-double-bold-false-italic-false-underline-false-strikethrough-false), [LookupGuiFont](../../maxgui/maxgui.maxgui/#function-lookupguifont-tguifont-pfonttype-guifont-system-pfontsize-double-0-pfontstyle-0), [RequestFont](../../maxgui/maxgui.maxgui/#function-requestfont-tguifont-font-tguifont-null), [FontSize](../../maxgui/maxgui.maxgui/#function-fontsize-double-font-tguifont) and [FontStyle](../../maxgui/maxgui.maxgui/#function-fontstyle-font-tguifont)


#### Returns
A string representing the name of the font.


<br/>

### `Function FontSize:Double(font:TGuiFont)`

Retrieves the corresponding property from the <b>TGuiFont</b> type instance.

See Also: [LoadGuiFont](../../maxgui/maxgui.maxgui/#function-loadguifont-tguifont-name-height-double-bold-false-italic-false-underline-false-strikethrough-false), [LookupGuiFont](../../maxgui/maxgui.maxgui/#function-lookupguifont-tguifont-pfonttype-guifont-system-pfontsize-double-0-pfontstyle-0), [RequestFont](../../maxgui/maxgui.maxgui/#function-requestfont-tguifont-font-tguifont-null), [FontName](../../maxgui/maxgui.maxgui/#function-fontname-font-tguifont) and [FontStyle](../../maxgui/maxgui.maxgui/#function-fontstyle-font-tguifont)


#### Returns
A double representing the size (in points) of the font.


<br/>

### `Function FontStyle(font:TGuiFont)`

Retrieves the corresponding property from the <b>TGuiFont</b> type instance.

The returned value will be a combination of the following bit flags:

<table><tr><td> <b>Constant</b></td><td><b>Font Style</b></td></tr><tr><td>  FONT_BOLD</td><td>Bold</td></tr><tr><td>  FONT_ITALIC</td><td>Italic</td></tr><tr><td>  FONT_UNDERLINE</td><td>Underlined</td></tr><tr><td>  FONT_STRIKETHROUGH</td><td>*Strikethrough</table>


<i>Note: FONT_STRIKETHROUGH isn't fully supported by all gadgets/platforms.</i>

See Also: [LoadGuiFont](../../maxgui/maxgui.maxgui/#function-loadguifont-tguifont-name-height-double-bold-false-italic-false-underline-false-strikethrough-false), [RequestFont](../../maxgui/maxgui.maxgui/#function-requestfont-tguifont-font-tguifont-null), [FontName](../../maxgui/maxgui.maxgui/#function-fontname-font-tguifont) and [FontSize](../../maxgui/maxgui.maxgui/#function-fontsize-double-font-tguifont)


#### Returns
An integer representing the style of the font (e.g. Bold, Underlined, Italics, Strikethrough).


<br/>

### `Function SetPointer(shape)`

Changes the applcation's mouse cursor.


The shape of the system mouse pointer can be one of the following:

<table><tr><td> <b>Constant</b></td><td><b>Description</b></td></tr><tr><td>  POINTER_DEFAULT</td><td>Default OS pointer.</td></tr><tr><td>  POINTER_ARROW</td><td>Arrow pointer.</td></tr><tr><td>  POINTER_IBEAM</td><td>Typically used when making text selections.</td></tr><tr><td>  POINTER_WAIT</td><td>Hourglass animation.</td></tr><tr><td>  POINTER_CROSS</td><td>Typically used for precise drawing.</td></tr><tr><td>  POINTER_UPARROW</td><td>Typically used for selections.</td></tr><tr><td>  POINTER_SIZENWSE</td><td>Typically used over sizing handles.</td></tr><tr><td>  POINTER_SIZENESW</td><td>Typically used over sizing handles.</td></tr><tr><td>  POINTER_SIZEWE</td><td>Typically used over sizing handles.</td></tr><tr><td>  POINTER_SIZENS</td><td>Typically used over sizing handles.</td></tr><tr><td>  POINTER_SIZEALL</td><td>Typically shown when moving an item.</td></tr><tr><td>  POINTER_NO</td><td>Typically shown when an action is prohibited.</td></tr><tr><td>  POINTER_HAND</td><td>Typically used for links.</td></tr><tr><td>  POINTER_APPSTARTING</td><td>Usually shows a pointer and miniature hourglass animation.</td></tr><tr><td>  POINTER_HELP</td><td>Usually shows an arrow pointer, with an adjacent question mark.</table>


<i>Note: Some pointers may not be supported on all platforms.</i>


#### Example
```blitzmax
' setpointer.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Local combo:TGadget

window=CreateWindow("SetPointer",40,40,320,240,,WINDOW_TITLEBAR)

CreateLabel "Select a pointer shape:",10,10,200,20,window

combo=CreateComboBox(10,30,200,24,window)
AddGadgetItem combo,"POINTER_DEFAULT"
AddGadgetItem combo,"POINTER_ARROW"
AddGadgetItem combo,"POINTER_IBEAM" 
AddGadgetItem combo,"POINTER_WAIT" 
AddGadgetItem combo,"POINTER_CROSS"
AddGadgetItem combo,"POINTER_UPARROW" 
AddGadgetItem combo,"POINTER_SIZENWSE" 
AddGadgetItem combo,"POINTER_SIZENESW" 
AddGadgetItem combo,"POINTER_SIZEWE" 
AddGadgetItem combo,"POINTER_SIZENS" 
AddGadgetItem combo,"POINTER_SIZEALL" 
AddGadgetItem combo,"POINTER_NO" 
AddGadgetItem combo,"POINTER_HAND"
AddGadgetItem combo,"POINTER_APPSTARTING"
AddGadgetItem combo,"POINTER_HELP"

SelectGadgetItem combo,0

While True
	WaitEvent 
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
		Case EVENT_GADGETACTION
			SetPointer EventData()
	End Select
Wend
```
<br/>

### `Function FreeGadget( gadget:TGadget )`

Remove a gadget and free its resources.

<br/>

### `Function ClientWidth( gadget:TGadget )`

Client area dimensions of a gadget.

#### Returns
The width of the client area (in pixels) of the specified container gadget.


<br/>

### `Function ClientHeight( gadget:TGadget )`

Client area dimensions of a gadget.

#### Returns
The height of the client area (in pixels) of the specified container gadget.


<br/>

### `Function GadgetX( gadget:TGadget )`

Horizontal position of gadget.

#### Returns
The horizontal position (in pixels) of a gadget relative to the top-left corner of the parent's client area.


<br/>

### `Function GadgetY( gadget:TGadget )`

Vertical position of gadget.

#### Returns
The vertical position (in pixels) of a gadget relative to the top-left corner of the parent's client area.


<br/>

### `Function GadgetWidth( gadget:TGadget )`

Gadget width.

#### Returns
The current width (in pixels) of a gadget.


<br/>

### `Function GadgetHeight( gadget:TGadget )`

Gadget height.

#### Returns
The current height (in pixels) of a gadget.


<br/>

### `Function GadgetGroup:TGadget( gadget:TGadget )`

Return a gadget's group or parent.

#### Returns
The <b>TGadget</b> instance of the parent or group gadget.


<br/>

### `Function GadgetClass( gadget:TGadget )`

Returns an integer representing a gadget's class.

The returned integer will match one of the following constants:

<table><tr><td> <b>Constant</b></td><td><b>Corresponding Gadget Class</b></td></tr><tr><td>  GADGET_DESKTOP</td><td>Desktop</td></tr><tr><td>  GADGET_WINDOW</td><td>Window</td></tr><tr><td>  GADGET_BUTTON</td><td>Button</td></tr><tr><td>  GADGET_PANEL</td><td>Panel</td></tr><tr><td>  GADGET_TEXTFIELD</td><td>TextField</td></tr><tr><td>  GADGET_TEXTAREA</td><td>TextArea</td></tr><tr><td>  GADGET_COMBOBOX</td><td>ComboBox</td></tr><tr><td>  GADGET_LISTBOX</td><td>ListBox</td></tr><tr><td>  GADGET_TOOLBAR</td><td>Toolbar</td></tr><tr><td>  GADGET_TABBER</td><td>Tabber</td></tr><tr><td>  GADGET_TREEVIEW</td><td>Treeview</td></tr><tr><td>  GADGET_HTMLVIEW</td><td>HtmlView</td></tr><tr><td>  GADGET_LABEL</td><td>Label</td></tr><tr><td>  GADGET_SLIDER</td><td>Slider</td></tr><tr><td>  GADGET_PROGBAR</td><td>Progress Bar</td></tr><tr><td>  GADGET_MENUITEM</td><td>Menu</td></tr><tr><td>  GADGET_NODE</td><td>Treeview Node</td></tr><tr><td>  GADGET_CANVAS</td><td>Canvas Gadget</table>




#### Example
```blitzmax
Strict

Import MaxGUI.Drivers

AppTitle = "GadgetClass() Example"
Global wndMain:TGadget = CreateWindow(AppTitle,100,100,220,200,Null,WINDOW_TITLEBAR|WINDOW_CLIENTCOORDS|WINDOW_STATUS)

	Global btnTest:TGadget = CreateButton("Push Button",10,10,200,30,wndMain,BUTTON_PUSH)
	Global chkTest:TGadget = CreateButton("Check Button",10,40,200,30,wndMain,BUTTON_CHECKBOX)
	
	Global cmbTest:TGadget = CreateComboBox(10,70,200,26,wndMain)
		AddGadgetItem(cmbTest,"Item 1");AddGadgetItem(cmbTest,"Item 2",GADGETITEM_DEFAULT);AddGadgetItem(cmbTest,"Item 3")
	
	Global sldTest:TGadget = CreateSlider(10,100,200,30,wndMain,SLIDER_HORIZONTAL|SLIDER_TRACKBAR)

Repeat

	WaitEvent()
	SetStatusText wndMain, CurrentEvent.ToString()
	
	Select EventID()
		
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE;End
		
		Case EVENT_GADGETACTION, EVENT_GADGETSELECT, EVENT_WINDOWMOVE, EVENT_WINDOWSIZE
			
			Select GadgetClass(TGadget(EventSource()))
				Case GADGET_WINDOW;Print "Window Event"
				Case GADGET_BUTTON;Print "Button Event"
				Case GADGET_COMBOBOX;Print "ComboBox Event"
				Case GADGET_SLIDER;Print "Slider Event"
			EndSelect
			
	EndSelect
	
Forever
```
<br/>

### `Function ShowGadget( gadget:TGadget )`

Make a gadget visible.

See Also: [HideGadget](../../maxgui/maxgui.maxgui/#function-hidegadget-gadget-tgadget) and [GadgetHidden](../../maxgui/maxgui.maxgui/#function-gadgethidden-gadget-tgadget-recursive-false).


<br/>

### `Function HideGadget( gadget:TGadget )`

Hide a gadget.

See Also: [ShowGadget](../../maxgui/maxgui.maxgui/#function-showgadget-gadget-tgadget) and [GadgetHidden](../../maxgui/maxgui.maxgui/#function-gadgethidden-gadget-tgadget-recursive-false).


<br/>

### `Function EnableGadget( gadget:TGadget )`

Enable a gadget, allowing user interaction.

See Also: [DisableGadget](../../maxgui/maxgui.maxgui/#function-disablegadget-gadget-tgadget) and [GadgetDisabled](../../maxgui/maxgui.maxgui/#function-gadgetdisabled-gadget-tgadget-recursive-false).


<br/>

### `Function DisableGadget( gadget:TGadget )`

Disable a gadget, blocking user interaction.

See Also: [EnableGadget](../../maxgui/maxgui.maxgui/#function-enablegadget-gadget-tgadget) and [GadgetDisabled](../../maxgui/maxgui.maxgui/#function-gadgetdisabled-gadget-tgadget-recursive-false).


<br/>

### `Function GadgetHidden( gadget:TGadget, recursive% = False )`

Determines whether a gadget is marked as hidden.

If the optional <b>recursive</b> parameter is set to [True](../../brl/brl.blitz/#true), the function will only return [False](../../brl/brl.blitz/#false)
if the gadget and all of its ancestors are visible, otherwise the function simply returns the
property of the individual gadget.

See Also: [ShowGadget](../../maxgui/maxgui.maxgui/#function-showgadget-gadget-tgadget) and [HideGadget](../../maxgui/maxgui.maxgui/#function-hidegadget-gadget-tgadget).


#### Returns
[True](../../brl/brl.blitz/#true) if the gadget is set to be hidden, [False](../../brl/brl.blitz/#false) otherwise.


<br/>

### `Function GadgetDisabled( gadget:TGadget, recursive% = False )`

Determines whether a gadget is marked as enabled.

If the optional <b>recursive</b> parameter is set to [True](../../brl/brl.blitz/#true), the function will only return [False](../../brl/brl.blitz/#false)
if the gadget and all of its ancestors are enabled, otherwise the function simply returns the
property of the individual gadget.

See Also: [EnableGadget](../../maxgui/maxgui.maxgui/#function-enablegadget-gadget-tgadget) and [DisableGadget](../../maxgui/maxgui.maxgui/#function-disablegadget-gadget-tgadget).


#### Returns
[True](../../brl/brl.blitz/#true) if the gadget is set to be disabled, [False](../../brl/brl.blitz/#false) otherwise.


<br/>

### `Function SetGadgetShape( gadget:TGadget,x,y,w,h )`

Set a gadget's size and position.

The position and size should be given in pixels, and are relative to the upper-left corner of its parent's client-area.

The <b>w</b> and <b>h</b> parameters set the gadget width or height, unless the gadget concerned is a window with the WINDOW_CLIENTCOORDS flag,
in which case, they represent the client-area dimensions.


<br/>

### `Function SetGadgetLayout( gadget:TGadget,Left,Right,Top,Bottom )`

Set the layout rules for a gadget when its parent is resized.


[SetGadgetLayout](../../maxgui/maxgui.maxgui/#function-setgadgetlayout-gadget-tgadget-left-right-top-bottom) lets you control the automatic layout of a gadget in the event that its parent is resized.

This will happen either if a window is resized, or if [SetGadgetShape](../../maxgui/maxgui.maxgui/#function-setgadgetshape-gadget-tgadget-x-y-w-h) is called on a group gadget.

Each edge of a <b>Gadget</b> has an alignment setting that fixes it in place in the following manner:

<table><tr><td> <b>Constant</b></td><td><b>Description</b></td></tr><tr><td>  EDGE_CENTERED</td><td>The edge of the gadget is kept a fixed distance from the center of its parent.</td></tr><tr><td>  EDGE_ALIGNED</td><td>The edge of the gadget stays a fixed distance from its parent's corresponding edge.</td></tr><tr><td>  EDGE_RELATIVE</td><td>The edge of the gadget remains a proportional distance from both of its parent's edges.</table>


The default behaviour may vary between platforms, so it is highly recommended that you set this for gadgets on resizable windows.


<br/>

### `Function SetGadgetSensitivity( gadget:TGadget, flags )`

Sets whether a standard MaxGUI gadget emits events from the keyboard or mouse.

This functions attempts to provide similar functionality for all gadgets to that of <b>Panels</b> created with the PANEL_ACTIVE flag.

The <b>flags</b> parameter can be any combination of the following:

SENSITIZE_MOUSE: The gadget will emit the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_MOUSEDOWN</td><td>Mouse button pressed. Event data contains mouse button code.</td></tr><tr><td>  EVENT_MOUSEUP</td><td>Mouse button released. Event data contains mouse button code.</td></tr><tr><td>  EVENT_MOUSEMOVE</td><td>Mouse moved. Event x and y contain mouse coordinates.</td></tr><tr><td>  EVENT_MOUSEWHEEL</td><td>Mouse wheel spun. Event data contains delta clicks.</td></tr><tr><td>  EVENT_MOUSEENTER</td><td>Mouse entered gadget area.</td></tr><tr><td>  EVENT_MOUSELEAVE</td><td>Mouse left gadget area.</table>


SENSITIZE_KEYS: The gadget will emit the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_KEYDOWN</td><td>Key pressed. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYUP</td><td>Key released. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYREPEAT</td><td>Key is being held down. Event data contains keycode.</table>


SENSITIZE_ALL: Exactly the same as combining SENSITIZE_MOUSE and SENSITIZE_KEYS.

Gadgets that have been disabled should not emit key events, although they may still emit mouse events.

Not all gadgets will be able to emit all of the events, particularly those that don't receive typical focus
such as labels or htmlviews, but even this may differ depending on the platform.

<i> <b>Warning:</b> This is a powerful new function that possibly involves hooking into the system's message queue
to ask for mouse/key events before they are processed even by the OS's GUI library. As such, using this function
on certain controls may cause them to be behave differently. In addition, care should be taken when using
this function to avoid infinite loops, for example repositioning gadgets in an event hook that processes the
message as it is received.

It is therefore recommended that this function is only used by advanced MaxGUI users.</i>

See Also: [GadgetSensitivity](../../maxgui/maxgui.maxgui/#function-gadgetsensitivity-gadget-tgadget)


<br/>

### `Function GadgetSensitivity( gadget:TGadget )`

Returns flags specifying whether a gadget emits events from the keyboard or mouse.

The function will return a combination of the following flags:

* SENSITIZE_MOUSE: The gadget will emit mouse events.
* SENSITIZE_KEYS: The gadget will emit keyboard events.

See [SetGadgetSensitivity](../../maxgui/maxgui.maxgui/#function-setgadgetsensitivity-gadget-tgadget-flags) for more information.


<br/>

### `Function SetGadgetExtra( gadget:TGadget, extra:Object )`

Stores a pointer to a related object, that can later be retrieved using [GadgetExtra](../../maxgui/maxgui.maxgui/#function-gadgetextra-object-gadget-tgadget).


This function has many uses - you may want to store a custom type instance to the treeview node that
represents it, or you may want to store a hidden string value that represents a gadget's action.

However, it is important to note that this function will result in a pointer being stored to that object
which will only be released when a new object or [Null](../../brl/brl.blitz/#null) is passed to this function, or when the gadget is freed
using [FreeGadget](../../maxgui/maxgui.maxgui/#function-freegadget-gadget-tgadget).


<br/>

### `Function GadgetExtra:Object( gadget:TGadget )`

Retrieves the object instance previously stored using [SetGadgetExtra](../../maxgui/maxgui.maxgui/#function-setgadgetextra-gadget-tgadget-extra-object).

<br/>

### `Function ActivateGadget( gadget:TGadget )`

Request focus for a gadget.

See Also: [ActiveGadget](../../maxgui/maxgui.maxgui/#function-activegadget-tgadget)()


<br/>

### `Function ActiveGadget:TGadget()`

Return the currently active gadget.

See Also: [ActivateGadget](../../maxgui/maxgui.maxgui/#function-activategadget-gadget-tgadget).


#### Returns
The gadget that currently has the keyboard focus. Returns [Null](../../brl/brl.blitz/#null) if no MaxGUI gadget has focus.


<br/>

### `Function GadgetCut( gadget:TGadget )`

Perform a cut operation on a gadget.

This is most commonly used on <b>TextAreas</b> to cut text that is currently selected.


<br/>

### `Function GadgetCopy( gadget:TGadget )`

Perform a copy operation on a gadget.

This is most commonly used on <b>TextAreas</b> to copy text that is currently selected.


<br/>

### `Function GadgetPaste( gadget:TGadget )`

Perform a paste operation on a gadget.

This is most commonly used on <b>TextAreas</b> to paste text into the gadget from the clipboard.


<br/>

### `Function GadgetPrint( gadget:TGadget )`

Perform a print operation on a gadget.

This function is currently only supported on <b>TextAreas</b> and <b>HTMLViews</b>.


<br/>

### `Function RedrawGadget( gadget:TGadget )`

Redraws a gadget.


The RedrawGadget command requests that the gadget should be redrawn by the underlying
Operating System but is not necessarily guaranteed to happen immediately.

In the case of a <b>Canvas</b> gadget an EVENT_GADGETPAINT event is emitted
when the Operating System begins the actual redraw. The following example
illustrates how to manage this feature:


#### Example
```blitzmax
' redrawgadget.bmx

' version 3 - fixed to be compatible with virtual resolutions

Import MaxGui.Drivers

Strict

Type TApplet 

	Method OnEvent(Event:TEvent) Abstract

	Method Run()
		AddHook EmitEventHook,eventhook,Self
	End Method

	Function eventhook:Object(id,data:Object,context:Object)
		Local event:TEvent = TEvent(data)
		Local app:TApplet = TApplet(context)
		app.OnEvent( event )
		Return data
	End Function

End Type

Type TSpinningApplet Extends TApplet
	
	Global image:TImage
	
	Field timer:TTimer
	Field window:TGadget, canvas:TGadget
	
	Method Draw()
		
		SetGraphics CanvasGraphics(canvas)
		SetVirtualResolution ClientWidth(canvas),ClientHeight(canvas)
		SetViewport 0,0,ClientWidth(canvas), ClientHeight(canvas)
		
		SetBlend( ALPHABLEND )
		SetRotation( MilliSecs()*.1 )
		SetClsColor( 255, 0, 0 )
		
		Cls()
		DrawImage( image, GraphicsWidth()/2, GraphicsHeight()/2 )
		
		Flip()
		
	End Method
	
	Method OnEvent(event:TEvent)
		If Not event Then Return 
		Select event.id
			Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE
				End
			Case EVENT_TIMERTICK
				RedrawGadget( canvas )
			Case EVENT_GADGETPAINT
				If (event.source = canvas) Then Draw()
		End Select
	End Method
	
	Method Create:TSpinningApplet(name$)
		
		If Not image Then image = LoadImage( "fltkwindow.png" )
		
		window = CreateWindow( name, 20, 20, 512, 512 )
		
		Local w = ClientWidth(window)
		Local h = ClientHeight(window)
		
		canvas = CreateCanvas( 0, 0, w, h, window )
		SetGadgetLayout( canvas, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED )
		
		timer = CreateTimer( 100 )
		Run()
		
		Return Self
		
	End Method
	
End Type

AutoMidHandle True

Local spinner:TSpinningApplet = New TSpinningApplet.Create("Spinning Applet")

Repeat
	WaitSystem()
Forever
```
<br/>

### `Function SetGadgetPixmap( gadget:TGadget, pixmap:TPixmap, flags% = GADGETPIXMAP_ICON )`

Set a gadget's pixmap.

This is a more generic form of old backwards-compatible [SetPanelPixmap](../../maxgui/maxgui.maxgui/#function-setpanelpixmap-panel-tgadget-pixmap-tpixmap-flags-panelpixmap-tile) function which now allows icons
to be set for other gadgets as well as just backgrounds for panels.

For setting background pixmaps on panels, <b>flags</b> should still be one of the following:

<table><tr><td> <b>Flag</b></td><td><b>Description</b></td></tr><tr><td>  PANELPIXMAP_TILE</td><td>The panel is filled with repeating tiles.</td></tr><tr><td>  PANELPIXMAP_CENTER</td><td>The pixmap is positioned at the center of the panel.</td></tr><tr><td>  PANELPIXMAP_FIT</td><td>The pixmap is scaled proportionally to best fit the panel size.</td></tr><tr><td>  PANELPIXMAP_FIT2</td><td>A variant of PANELPIXMAP_FIT where clipping can occur to achieve a better fit.</td></tr><tr><td>  PANELPIXMAP_STRETCH</td><td>The pixmap is stretched to fit the entire panel.</table>


Alternatively, to set a push-button or menu's icon, use the following constants:

<table><tr><td> <b>Flag</b></td><td><b>Description</b></td></tr><tr><td>  GADGETPIXMAP_ICON</td><td>Places an icon-sized pixmap onto a push-button/menu.</td></tr><tr><td>  GADGETPIXMAP_NOTEXT</td><td>Removes text on buttons when used in conjunction with GADGETPIXMAP_ICON.</table>


Each platform allows slightly different maximum icon sizes for their menus. Therefore, the recommended
size for menu icons is 12x12 pixels which appears to work well on all supported platforms.

Note: At present, OK buttons do not support icons as a cross-platform solution is unavailable. Icons
are also not supported for radio buttons or checkbox style buttons.

Passing [Null](../../brl/brl.blitz/#null) as the value for the <b>pixmap</b> parameter will remove the pixmap from the gadget.


<br/>

### `Function SetGadgetAlpha( gadget:TGadget,alpha# )`

Set the transparency of a gadget.

Alpha should be in the range 0.0 (invisible) to 1.0 (solid). Very few gadgets support this functionality,
but some Mac OS X gadgets do, in addition to <b>Windows</b> when running Windows XP+. In certain circumstances, window
transparency may be disabled (for example, when a canvas is added to a window) to prevent redraw issues on some
platforms.

Using the function on windows with <b>Canvases</b> on them may cause undesired effects, particularly on Windows 2000/XP
because of conflicts between the software based window manager and the hardware accelerated graphics contexts.


<br/>

### `Function SetGadgetText( gadget:TGadget,Text$ )`

Sets a gadget's text.

For the <b>Label</b>, <b>Button</b>, <b>TextField</b>, <b>ComboBox</b>, <b>TextArea</b> and Group <b>Panel</b> gadgets, the contents
of the gadget are replaced with the new <b>text</b>$.

For a <b>Window</b> gadget, [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text) changes the title. For <b>Window</b>s with a status bar, [SetStatusText](../../maxgui/maxgui.maxgui/#function-setstatustext-window-tgadget-text)
should be used to independently set the status bar text.

This command will automatically delocalize the gadget - to set localized gadget text, see [LocalizeGadget](../../maxgui/maxgui.maxgui/#function-localizegadget-gadget-tgadget-localizationtext-localizationtooltip).


<br/>

### `Function GadgetText$( gadget:TGadget )`

Returns a gadget's text.

For the <b>Label</b>, <b>Button</b>, <b>TextField</b>, <b>ComboBox</b>, <b>TextArea</b> and Group <b>Panel</b> gadgets, the contents
of the gadget are returned with the new gadget's text.

For a <b>Window</b> gadget, [GadgetText](../../maxgui/maxgui.maxgui/#function-gadgettext-gadget-tgadget) returns the title of the <b>Window</b>.


<br/>

### `Function SetGadgetToolTip( gadget:TGadget, tip$ )`

Set a gadget's tooltip.

Sets the tooltip for a <i>non-item based</i> positionable MaxGUI gadget. This function will have no effect on the following gadget types:

* Windows
* Menus
* Tree-view nodes
* List-boxes
* Toolbars
* Tabbers
* Desktops

This command will automatically delocalize the gadget - to set a localized gadget tooltip, see [LocalizeGadget](../../maxgui/maxgui.maxgui/#function-localizegadget-gadget-tgadget-localizationtext-localizationtooltip).

See Also: [GadgetTooltip](../../maxgui/maxgui.maxgui/#function-gadgettooltip-gadget-tgadget)()


<br/>

### `Function GadgetTooltip$( gadget:TGadget )`

Returns the gadget tooltip previously set with [SetGadgetTooltip](../../maxgui/maxgui.maxgui/#function-setgadgettooltip-gadget-tgadget-tip).

Returns the tooltip for a <i>non-item based</i> positionable MaxGUI gadget. As such, this function will have no effect on the following gadget types:

* Windows
* Menus
* Tree-view nodes
* List-boxes
* Toolbars
* Tabbers
* Desktops

See Also: [SetGadgetTooltip](../../maxgui/maxgui.maxgui/#function-setgadgettooltip-gadget-tgadget-tip)()


<br/>

### `Function SetGadgetFont( gadget:TGadget,font:TGuiFont, applyToChildren:Int = False )`

Set a gadget's font.

See [LoadGuiFont](../../maxgui/maxgui.maxgui/#function-loadguifont-tguifont-name-height-double-bold-false-italic-false-underline-false-strikethrough-false) and [RequestFont](../../maxgui/maxgui.maxgui/#function-requestfont-tguifont-font-tguifont-null) for creating a <b>TGuiFont</b>.


<br/>

### `Function SetGadgetTextColor( gadget:TGadget,r,g,b )`

Set a gadget's foreground color.

The <b>r</b>ed, <b>g</b>reen and <b>b</b>lue components should be in the range 0 to 255.
See Also: [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true)()


<br/>

### `Function SetGadgetColor( gadget:TGadget,r,g,b,bg=True )`

Set a gadget's background color.

The <b>r</b>ed, <b>g</b>reen and <b>b</b>lue components should be in the range 0 to 255.
This command is not supported for all Gadget types on all platforms.
See Also: [SetGadgetTextColor](../../maxgui/maxgui.maxgui/#function-setgadgettextcolor-gadget-tgadget-r-g-b)() [SetGadgetAlpha](../../maxgui/maxgui.maxgui/#function-setgadgetalpha-gadget-tgadget-alpha) [RemoveGadgetColor](../../maxgui/maxgui.maxgui/#function-removegadgetcolor-gadget-tgadget)


<br/>

### `Function RemoveGadgetColor( gadget:TGadget )`

Removes a gadget's background color.

Restores a gadget to it's default color.
See Also: [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true)()


<br/>

### `Function SetGadgetHotKey( gadget:TGadget,hotkey,modifier )`

Set the hot-key combination for a gadget.

<br/>

### `Function SetGadgetFilter( gadget:TGadget,callback(event:TEvent,context:Object),context:Object=Null )`

Attaches an event filter function to a MaxGUI gadget.


The filter function supplied is called by the gadget with a [TEvent](../../brl/brl.event/tevent)
and optional user context object. If the function returns zero the event
is filtered and not processed further by the system whereas a non zero
return indicates event processing should proceed as normal.

The TextArea/TextField events currently supported:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_KEYDOWN</td><td>Key pressed. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYCHAR</td><td>Key character. Event data contains unicode value.</table>


Currently only the EVENT_KEYDOWN, EVENT_KEYCHAR events produced by
TextArea and TextField gadgets can be filtered with the SetGadgetFilter
command.


#### Example
```blitzmax
' setgadgetfilter.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Global textarea:TGadget

window=CreateWindow("My Window",30,20,320,240)

textarea=CreateTextArea(0,24,ClientWidth(window),ClientHeight(window)-24,window)

SetGadgetLayout textarea,1,1,1,1
SetGadgetText textarea,"A textarea gadget that filters out down arrowsnand tab keys."
ActivateGadget textarea

SetGadgetFilter textarea,filter

Print "KEY_TAB="+KEY_TAB

Function filter(event:TEvent,context:Object)
	Select event.id
		Case EVENT_KEYDOWN
			Print "filtering keydown:"+event.data+","+event.mods
			If event.data=KEY_DOWN Return 0
			If event.data=13 Return 0
		Case EVENT_KEYCHAR
			Print "filtering charkey:"+event.data+","+event.mods
			If event.data=KEY_TAB Return 0
	End Select
	Return 1
End Function

While WaitEvent()
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
	End Select
Wend
```
<br/>

### `Function LocalizeGadget( gadget:TGadget, localizationtext$, localizationtooltip$ = "" )`

Localize a gadget using the supplied localization strings.

The function will use the supplied localization strings to localize a gadget and its text.  The gadget
will also be marked so that changing the language will update the text.  Calling [DelocalizeGadget](../../maxgui/maxgui.maxgui/#function-delocalizegadget-gadget-tgadget) or
[SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text) will disable this behaviour.

Localization strings and their structure are described in [LocalizeString](../../maxgui/maxgui.localization/#function-localizestring-localizationstring) function documentation.

Item-based gadgets should mark any items, whose strings are also wanted to be localized, with the
GADGETITEM_LOCALIZED flag.  See the <b>flags</b> parameter of the [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null) / [InsertGadgetItem](../../maxgui/maxgui.maxgui/#function-insertgadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null)
/ [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null) calls.

See Also: [GadgetLocalized](../../maxgui/maxgui.maxgui/#function-gadgetlocalized-int-gadget-tgadget), [SetLocalizationMode](../../maxgui/maxgui.localization/#function-setlocalizationmode-mode-int-localization-on) and [SetLocalizationLanguage](../../maxgui/maxgui.localization/#function-setlocalizationlanguage-language-tmaxguilanguage).


<br/>

### `Function GadgetLocalized:Int( gadget:TGadget )`

Determines whether a gadget is registered as being 'localized'.

See [LocalizeGadget](../../maxgui/maxgui.maxgui/#function-localizegadget-gadget-tgadget-localizationtext-localizationtooltip) and [SetLocalizationMode](../../maxgui/maxgui.localization/#function-setlocalizationmode-mode-int-localization-on) for more information.


<br/>

### `Function DelocalizeGadget( gadget:TGadget )`

Delocalizes a gadget so that it's no longer updated if the localization language/mode changes.

See Also: [LocalizeGadget](../../maxgui/maxgui.maxgui/#function-localizegadget-gadget-tgadget-localizationtext-localizationtooltip), [SetLocalizationLanguage](../../maxgui/maxgui.localization/#function-setlocalizationlanguage-language-tmaxguilanguage) and [SetLocalizationMode](../../maxgui/maxgui.localization/#function-setlocalizationmode-mode-int-localization-on).


<br/>

### `Function CreateMenu:TGadget( Text$,tag,parent:TGadget,hotkey=0,modifier=0 )`

Creates a new menu item.

Menu gadgets should be attached to either a [WindowMenu](../../maxgui/maxgui.maxgui/#function-windowmenu-tgadget-window-tgadget), other Menu gadgets
or used with the [PopupWindowMenu](../../maxgui/maxgui.maxgui/#function-popupwindowmenu-window-tgadget-menu-tgadget-extra-object-null) command. The tag field should be a unique identifier
that will be present in the [EventData](../../brl/brl.eventqueue/#function-eventdata-int) field of EVENT_MENUACTION events.

Keyboard shortcuts can be associated with a Menu by using the optional hotKey and
modifier parameters.

Please refer to the key codes module for valid key and modifier codes.
The MODIFIER_COMMAND value should be used instead of MODIFIER_CONTROL
with Menu hotkeys for best crossplatform compatability.

Menus now also support icons on most platforms through the use of [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon).

See Also: [FreeMenu](../../maxgui/maxgui.maxgui/#function-freemenu-menu-tgadget), [SetMenuText](../../maxgui/maxgui.maxgui/#function-setmenutext-menu-tgadget-text), [CheckMenu](../../maxgui/maxgui.maxgui/#function-checkmenu-menu-tgadget), [UncheckMenu](../../maxgui/maxgui.maxgui/#function-uncheckmenu-menu-tgadget), [EnableMenu](../../maxgui/maxgui.maxgui/#function-enablemenu-menu-tgadget), [DisableMenu](../../maxgui/maxgui.maxgui/#function-disablemenu-menu-tgadget),
[MenuText](../../maxgui/maxgui.maxgui/#function-menutext-menu-tgadget), [MenuChecked](../../maxgui/maxgui.maxgui/#function-menuchecked-menu-tgadget), [MenuEnabled](../../maxgui/maxgui.maxgui/#function-menuenabled-menu-tgadget) and [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon).


#### Example
```blitzmax
' createmenu.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Local filemenu:TGadget
Local editmenu:TGadget
Local helpmenu:TGadget

Const MENU_NEW=101
Const MENU_OPEN=102
Const MENU_SAVE=103
Const MENU_CLOSE=104
Const MENU_EXIT=105

Const MENU_CUT=106
Const MENU_COPY=107
Const MENU_PASTE=108

Const MENU_ABOUT=109

window=CreateWindow("My Window",40,40,320,240)

filemenu=CreateMenu("&File",0,WindowMenu(window))
CreateMenu"&New",MENU_NEW,filemenu,KEY_N,MODIFIER_COMMAND
CreateMenu"&Open",MENU_OPEN,filemenu,KEY_O,MODIFIER_COMMAND
CreateMenu"&Close",MENU_CLOSE,filemenu,KEY_W,MODIFIER_COMMAND
CreateMenu"",0,filemenu
CreateMenu"&Save",MENU_SAVE,filemenu,KEY_S,MODIFIER_COMMAND
Local saves:TGadget = CreateMenu("Save More",0,filemenu)
CreateMenu"",0,filemenu
CreateMenu"E&xit",MENU_EXIT,filemenu,KEY_F4,MODIFIER_COMMAND

editmenu=CreateMenu("&Edit",0,WindowMenu(window))
CreateMenu "Cu&t",MENU_CUT,editmenu,KEY_X,MODIFIER_COMMAND
CreateMenu "&Copy",MENU_COPY,editmenu,KEY_C,MODIFIER_COMMAND
CreateMenu "&Paste",MENU_PASTE,editmenu,KEY_V,MODIFIER_COMMAND

helpmenu=CreateMenu("&Help",0,WindowMenu(window))
CreateMenu "&About",MENU_ABOUT,helpmenu

CreateMenu("Option 1", 110,saves)
Local opt:TGadget = CreateMenu("Option 2", 111,saves)

UpdateWindowMenu window

While True
	WaitEvent 
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
		Case EVENT_MENUACTION
			Select EventData()
				Case MENU_EXIT
					End
				Case MENU_ABOUT
					Notify "Incrediablern(C)2005 Incredible Software"
				Case 111
					CheckMenu(opt)
			End Select
	End Select
Wend
```
<br/>

### `Function FreeMenu( menu:TGadget )`

Remove a menu.

This function has been superseded by [FreeGadget](../../maxgui/maxgui.maxgui/#function-freegadget-gadget-tgadget), but is available for backwards compatability.


<br/>

### `Function SetMenuText( menu:TGadget,Text$ )`

Modify a menu's text.

This function has been superseded by [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), but is available for backwards compatability.


<br/>

### `Function CheckMenu( menu:TGadget )`

Set a menu's checked state.

[UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget) should be called where appropriate after changing a menu's state for the changes
to become visible.


<br/>

### `Function UncheckMenu( menu:TGadget )`

Clear a menu's checked state.

[UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget) should be called where appropriate after changing a menu's state for the changes
to become visible.


<br/>

### `Function EnableMenu( menu:TGadget )`

Enable a menu for selection.

[UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget) should be called where appropriate after changing a menu's status for the changes
to become visible.


<br/>

### `Function DisableMenu( menu:TGadget )`

Disable a menu so it cannot be selected.

[UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget) should be called where appropriate after changing a menu's status for the changes
to become visible.


<br/>

### `Function MenuText$( menu:TGadget )`

Return a menu's text.

This function has been superseded by [GadgetText](../../maxgui/maxgui.maxgui/#function-gadgettext-gadget-tgadget), but is available for backwards compatability.


<br/>

### `Function MenuChecked( menu:TGadget )`

Return a menu's checked state.

<br/>

### `Function MenuEnabled( menu:TGadget )`

Return a menu's enabled state.

<br/>

### `Function Desktop:TGadget()`

Return a gadget representing the system's desktop.

This is particularly useful for finding the resolution of the desktop using [GadgetWidth](../../maxgui/maxgui.maxgui/#function-gadgetwidth-gadget-tgadget) / [ClientWidth](../../maxgui/maxgui.maxgui/#function-clientwidth-gadget-tgadget) or [GadgetHeight](../../maxgui/maxgui.maxgui/#function-gadgetheight-gadget-tgadget) / [ClientHeight](../../maxgui/maxgui.maxgui/#function-clientheight-gadget-tgadget).


<br/>

### `Function CreateWindow:TGadget( titletext$,x,y,w,h,group:TGadget=Null,style=WINDOW_DEFAULT )`

Create a Window gadget.


A Window is the primary gadget of MaxGUI. Windows should be used as the primary
group gadgets in MaxGUI applications to contain the gadgets that make up the program's
user interface.

The following style flags are supported when creating a Window. Any of the
style flags can be combined using the bitwise operator '|'.

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  WINDOW_TITLEBAR</td><td>The Window has a titlebar that displays the <b>titletext</b>$.</td></tr><tr><td>  WINDOW_RESIZABLE</td><td>The Window can be resized by the user.</td></tr><tr><td>  WINDOW_MENU</td><td>The Window has an associated window menu (retrieve menu handle using [WindowMenu](../../maxgui/maxgui.maxgui/#function-windowmenu-tgadget-window-tgadget)).</td></tr><tr><td>  WINDOW_STATUS</td><td>The Window has a statusbar.</td></tr><tr><td>  WINDOW_TOOL</td><td>A window style commonly used for toolbars and other tool windows.</td></tr><tr><td>  WINDOW_CLIENTCOORDS</td><td>The dimensions specified relate to the client area as opposed to the window frame.</td></tr><tr><td>  WINDOW_CENTER</td><td>The x and y parameters are ignored, and the Window is positioned either in the middle of the screen or the middle of the parent gadget.</td></tr><tr><td>  WINDOW_HIDDEN</td><td>The Window is created in a hidden state and can be revealed later using [ShowGadget](../../maxgui/maxgui.maxgui/#function-showgadget-gadget-tgadget).</td></tr><tr><td>  WINDOW_ACCEPTFILES</td><td>Enable file drag and drop operations (emits the EVENT_WINDOWACCEPT events).</table>


Note: For cross-platform projects, it is highly recommended that the WINDOW_CLIENTCOORDS style is used to maintain
similar layouts with different operating systems and window managers.

The default window style (WINDOW_DEFAULT) is equivalent to WINDOW_TITLEBAR | WINDOW_RESIZABLE | WINDOW_MENU | WINDOW_STATUS.

A Window emits the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_WINDOWMOVE</td><td>Window has been moved.</td></tr><tr><td>  EVENT_WINDOWSIZE</td><td>Window has been resized.</td></tr><tr><td>  EVENT_WINDOWCLOSE</td><td>Window close icon clicked.</td></tr><tr><td>  EVENT_WINDOWACTIVATE</td><td>Window has been activated.</td></tr><tr><td>  EVENT_WINDOWACCEPT</td><td>A file was dropped onto a Window with the WINDOW_ACCEPTFILES style. The event <b>Extra</b> object holds the filepath.</table>


See Also: [WindowMenu](../../maxgui/maxgui.maxgui/#function-windowmenu-tgadget-window-tgadget), [UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget), [PopupWindowMenu](../../maxgui/maxgui.maxgui/#function-popupwindowmenu-window-tgadget-menu-tgadget-extra-object-null), [ActivateWindow](../../maxgui/maxgui.maxgui/#function-activatewindow-window-tgadget), [SetStatusText](../../maxgui/maxgui.maxgui/#function-setstatustext-window-tgadget-text), [WindowStatusText](../../maxgui/maxgui.maxgui/#function-windowstatustext-window-tgadget),
[SetMinWindowSize](../../maxgui/maxgui.maxgui/#function-setminwindowsize-window-tgadget-w-h), [SetMaxWindowSize](../../maxgui/maxgui.maxgui/#function-setmaxwindowsize-window-tgadget-w-h), [MinimizeWindow](../../maxgui/maxgui.maxgui/#function-minimizewindow-window-tgadget), [MaximizeWindow](../../maxgui/maxgui.maxgui/#function-maximizewindow-window-tgadget), [RestoreWindow](../../maxgui/maxgui.maxgui/#function-restorewindow-window-tgadget), [WindowMinimized](../../maxgui/maxgui.maxgui/#function-windowminimized-window-tgadget)
and [WindowMaximized](../../maxgui/maxgui.maxgui/#function-windowmaximized-window-tgadget).


#### Example
```blitzmax
' createwindow.bmx

Import MaxGui.Drivers

Strict 

AppTitle = "CreateWindow() Example"

Global FLAGS:Int

' Comment/uncomment any of the following lines to experiment with the different styles.

FLAGS:| WINDOW_TITLEBAR
FLAGS:| WINDOW_RESIZABLE
FLAGS:| WINDOW_MENU
FLAGS:| WINDOW_STATUS
FLAGS:| WINDOW_CLIENTCOORDS
'FLAGS:| WINDOW_HIDDEN
FLAGS:| WINDOW_ACCEPTFILES
'FLAGS:| WINDOW_TOOL
'FLAGS:| WINDOW_CENTER

Local window:TGadget = CreateWindow( AppTitle, 100, 100, 320, 240, Null, FLAGS )

If (FLAGS & WINDOW_STATUS) Then
	SetStatusText( window, "Left alignedtCenter alignedtRight aligned" )
EndIf

Repeat
	WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_APPTERMINATE, EVENT_WINDOWCLOSE
			End
	End Select
Forever
```
<br/>

### `Function WindowMenu:TGadget( window:TGadget )`

Returns a window's main-menu handle.

Required when a root menu is to be added to a window using [CreateMenu](../../maxgui/maxgui.maxgui/#function-createmenu-tgadget-text-tag-parent-tgadget-hotkey-0-modifier-0). This function
should <i>not</i> be used for sub-menus - the sub-menu should be parented directly to its parent menu.

It should also be mentioned that this function isn't required when creating popup menus - [Null](../../brl/brl.blitz/#null) should
instead be passed as the parent of the root menu.

To avoid any unexpected behavior, make sure that the window specified was created with the WINDOW_MENU
style flag.

See Also: [CreateMenu](../../maxgui/maxgui.maxgui/#function-createmenu-tgadget-text-tag-parent-tgadget-hotkey-0-modifier-0) and [UpdateWindowMenu](../../maxgui/maxgui.maxgui/#function-updatewindowmenu-window-tgadget)


<br/>

### `Function UpdateWindowMenu( window:TGadget )`

Update a window's menu hierachy.

Required after changing a window's menu properties/structure for the changes to become visible.

To avoid any unexpected behavior, make sure that the window specified was created with the WINDOW_MENU
style flag.

See Also: [WindowMenu](../../maxgui/maxgui.maxgui/#function-windowmenu-tgadget-window-tgadget) and [CreateMenu](../../maxgui/maxgui.maxgui/#function-createmenu-tgadget-text-tag-parent-tgadget-hotkey-0-modifier-0)


<br/>

### `Function PopupWindowMenu( window:TGadget,menu:TGadget,extra:Object=Null )`

Display a popup menu.

A popup context-menu is displayed on the screen at the user's current mouse position.
See Also: [CreateMenu](../../maxgui/maxgui.maxgui/#function-createmenu-tgadget-text-tag-parent-tgadget-hotkey-0-modifier-0)


#### Example
```blitzmax
Strict

Import MaxGui.Drivers

Local menu:TGadget
Local window:TGadget
Local panel:TGadget

menu=CreateMenu("popup",0,Null)
CreateMenu("Load",101,menu)
CreateMenu("Save",102,menu)

window=CreateWindow("Test PopupWindowMenu",20,20,200,200)

' create a panel to capture some mouse events

panel=CreatePanel(0,0,ClientWidth(window),ClientHeight(window),window,PANEL_ACTIVE)

While True
	WaitEvent
	Select EventID()
		Case EVENT_MOUSEDOWN
			If EventData()=2 PopupWindowMenu window,menu
		Case EVENT_WINDOWCLOSE
			End
		Case EVENT_MENUACTION
			Print "EVENT_MENUACTION: eventdata()="+EventData()
	End Select
Wend
```
<br/>

### `Function ActivateWindow( window:TGadget )`

Activate a window gadget.

This function has been superseded by [ActivateGadget](../../maxgui/maxgui.maxgui/#function-activategadget-gadget-tgadget), but is available for backwards compatability.


<br/>

### `Function WindowStatusText$( window:TGadget )`

Retrieve a window's status-bar text.

Can only be used with windows created with the WINDOW_STATUS flag (see [CreateWindow](../../maxgui/maxgui.maxgui/#function-createwindow-tgadget-titletext-x-y-w-h-group-tgadget-null-style-window-default)). Tab characters
delimit between the three alignments of text.  See [SetStatusText](../../maxgui/maxgui.maxgui/#function-setstatustext-window-tgadget-text) for more information.


<br/>

### `Function SetStatusText( window:TGadget,Text$ )`

Set a window's status bar text.

Can only be used with windows created with the WINDOW_STATUS flag (see [CreateWindow](../../maxgui/maxgui.maxgui/#function-createwindow-tgadget-titletext-x-y-w-h-group-tgadget-null-style-window-default)). Use tab characters
to delimit between the three alignments of text.  For example:

```
SetStatusText( window, "Left Aligned Only" )
SetStatusText( window, "Left Aligned~tCenter Aligned~tRight Aligned" )
SetStatusText( window, "~tCenter Aligned Only" )
SetStatusText( window, "~t~tRight Aligned Only" )
````


See Also: [WindowStatusText](../../maxgui/maxgui.maxgui/#function-windowstatustext-window-tgadget)


<br/>

### `Function SetMinWindowSize( window:TGadget,w,h )`

Set a window's minimum size.

Only useful for resizable windows (i.e. windows created with the WINDOW_RESIZABLE flag, see [CreateWindow](../../maxgui/maxgui.maxgui/#function-createwindow-tgadget-titletext-x-y-w-h-group-tgadget-null-style-window-default)).


<br/>

### `Function SetMaxWindowSize( window:TGadget,w,h )`

Set a window's maximum size.

Only useful for resizable windows (i.e. windows created with the WINDOW_RESIZABLE flag, see [CreateWindow](../../maxgui/maxgui.maxgui/#function-createwindow-tgadget-titletext-x-y-w-h-group-tgadget-null-style-window-default)).

Calling this function will disable the Maximize button window hint on Windows, and will limit the window zoom size on Mac OS X.


<br/>

### `Function MinimizeWindow( window:TGadget )`

Minimize a window.

A minimized window can be restored by the user to its previous state, typically by clicking on the icon representation
of the window in the taskbar or dock.  The same effect can be obtained programatically by calling [RestoreWindow](../../maxgui/maxgui.maxgui/#function-restorewindow-window-tgadget).

See Also: [WindowMinimized](../../maxgui/maxgui.maxgui/#function-windowminimized-window-tgadget).


<br/>

### `Function MaximizeWindow( window:TGadget )`

Maximize a window.


Maximizing a window makes the window visible and sizes it to fill the current desktop.  [RestoreWindow](../../maxgui/maxgui.maxgui/#function-restorewindow-window-tgadget) can be used to
programatically restore a window to its previous unmaximized state, although the window will still remain unhidden.

See Also: [WindowMaximized](../../maxgui/maxgui.maxgui/#function-windowmaximized-window-tgadget).


<br/>

### `Function RestoreWindow( window:TGadget )`

Restore a window from a minimized or maximized state.

See Also: [MinimizeWindow](../../maxgui/maxgui.maxgui/#function-minimizewindow-window-tgadget) and [MaximizeWindow](../../maxgui/maxgui.maxgui/#function-maximizewindow-window-tgadget).


<br/>

### `Function WindowMinimized( window:TGadget )`

Detect if a window is minimized.

#### Returns
[True](../../brl/brl.blitz/#true) if the window is currently minimized, [False](../../brl/brl.blitz/#false) if not.


<br/>

### `Function WindowMaximized( window:TGadget )`

Detect if a window is maximized.

A maximized window fills the entire desktop. A window may
be maximized with the [MaximizeWindow](../../maxgui/maxgui.maxgui/#function-maximizewindow-window-tgadget) command or by the user if
[CreateWindow](../../maxgui/maxgui.maxgui/#function-createwindow-tgadget-titletext-x-y-w-h-group-tgadget-null-style-window-default) was called with the WINDOW_RESIZABLE flag.


#### Returns
[True](../../brl/brl.blitz/#true) if the window is currently maximized, [False](../../brl/brl.blitz/#false) if not.


<br/>

### `Function CreateButton:TGadget(label$,x,y,w,h,group:TGadget,style=BUTTON_PUSH)`

Create a Button gadget.


A Button generates an EVENT_GADGETACTION [TEvent](../../brl/brl.event/tevent) whenever it is pushed.

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  BUTTON_PUSH</td><td>Standard push button.</td></tr><tr><td>  BUTTON_CHECKBOX</td><td>A check box button that displays a tick when its state is [True](../../brl/brl.blitz/#true).</td></tr><tr><td>  BUTTON_RADIO</td><td>A radio button is accompanied by a small circular indicator, filled when its state is [True](../../brl/brl.blitz/#true).</td></tr><tr><td>  BUTTON_OK</td><td>Standard push button that is also activated when the user presses the RETURN key.</td></tr><tr><td>  BUTTON_CANCEL</td><td>Standard push button that is also activated when the user presses the ESCAPE key.</table>


On certain platforms, the BUTTON_PUSH flag can be combined with either BUTTON_CHECKBOX or BUTTON_RADIO to obtain
a button looking similar to standard push-buttons, but mimicking the behaviour of the checkbox or radio button.

See Also: [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), [SetButtonState](../../maxgui/maxgui.maxgui/#function-setbuttonstate-button-tgadget-checked), [ButtonState](../../maxgui/maxgui.maxgui/#function-buttonstate-button-tgadget) and [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon).


#### Example
```blitzmax
' createbutton.bmx

Import MaxGui.Drivers

Strict 

Global window:TGadget = CreateWindow("MaxGUI Buttons",40,40,400,330,Null,WINDOW_TITLEBAR|WINDOW_CLIENTCOORDS)
	CreateButton("Std. Button",10,10,120,30,window,BUTTON_PUSH)
	CreateButton("OK Button",140,10,120,30,window,BUTTON_OK)
	CreateButton("Cancel Button",270,10,120,30,window,BUTTON_CANCEL)

Global panel:TGadget[4]
	panel[0]=CreatePanel(10,50,380,60,window,PANEL_GROUP,"Checkbox")
		FillPanelWithButtons(panel[0], BUTTON_CHECKBOX, "Checkbox")
	panel[1]=CreatePanel(10,120,380,60,window,PANEL_GROUP,"Checkbox (with Push Button Style)")
		FillPanelWithButtons(panel[1], BUTTON_CHECKBOX|BUTTON_PUSH, "Toggle")
	panel[2]=CreatePanel(10,190,380,60,window,PANEL_GROUP,"Radio Buttons")
		FillPanelWithButtons(panel[2], BUTTON_RADIO, "Option ")
	panel[3]=CreatePanel(10,260,380,60,window,PANEL_GROUP,"Radio Buttons (with Push Button Style)")
		FillPanelWithButtons(panel[3], BUTTON_RADIO|BUTTON_PUSH, "Option")

Repeat
	Select WaitEvent()
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE
			End
		Case EVENT_GADGETACTION
			Print "EVENT_GADGETACTIONn" + ..
			"GadgetText(): q" + GadgetText(TGadget(EventSource())) + "q t " + ..
			"ButtonState(): "+ ButtonState(TGadget(EventSource()))
	EndSelect
Forever

Function FillPanelWithButtons( pPanel:TGadget, pStyle%, pText$ = "Button" )
	Local buttonwidth% = (pPanel.width-10)/3
	For Local i% = 0 Until 3
		CreateButton( pText + " " + (i+1), 5+(i*buttonwidth), 5, buttonwidth-10, 26, pPanel, pStyle )
	Next
EndFunction
```
<br/>

### `Function SetButtonState( button:TGadget,checked )`

Set a button's state.


Buttons created with the BUTTON_CHECKBOX and BUTTON_RADIO styles are able to show a selected state.
In addition, the BUTTON_CHECKBOX style may also be able to distinguish an indeterminate state from that
of a checked state through the use of the CHECK_INDETERMINATE (-1) constant, depending on the platform.

See Also: [CreateButton](../../maxgui/maxgui.maxgui/#function-createbutton-tgadget-label-x-y-w-h-group-tgadget-style-button-push), [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), [ButtonState](../../maxgui/maxgui.maxgui/#function-buttonstate-button-tgadget) and [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon).


<br/>

### `Function ButtonState( button:TGadget )`

Retrieve a button's state.


Returns a non-zero value if a checkbox or radio button is selected or false if it isn't.
On certain platforms, if a checkbox is set using [SetButtonState](../../maxgui/maxgui.maxgui/#function-setbuttonstate-button-tgadget-checked) to have an indeterminant
state (CHECK_INDETERMINATE), then this function will return CHECK_INDETERMINATE too.
See Also: [CreateButton](../../maxgui/maxgui.maxgui/#function-createbutton-tgadget-label-x-y-w-h-group-tgadget-style-button-push), [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), [SetButtonState](../../maxgui/maxgui.maxgui/#function-setbuttonstate-button-tgadget-checked) and [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon).


<br/>

### `Function CreatePanel:TGadget(x,y,w,h,group:TGadget,style=0,title$="")`

Create a Panel gadget.


A Panel is a general purpose gadget that can be used to group other gadgets.

Background colours and images can be set using [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true) and [SetPanelPixmap](../../maxgui/maxgui.maxgui/#function-setpanelpixmap-panel-tgadget-pixmap-tpixmap-flags-panelpixmap-tile).

A panel can be created with any one of the following <i>optional</i> styles:

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  PANEL_SUNKEN</td><td>Panel is drawn with a sunken border (or just a simple border on OS X).</td></tr><tr><td>  PANEL_RAISED</td><td>Panel is drawn with a raised border (or just a simple border on OS X).</td></tr><tr><td>  PANEL_GROUP</td><td>Panel is drawn with a titled etched border.</table>


The PANEL_ACTIVE flag can be combined with any other style flags, or specified on its own,
to generate mouse and key events (equivalent to calling [SetGadgetSensitivity](../../maxgui/maxgui.maxgui/#function-setgadgetsensitivity-gadget-tgadget-flags) immediately
after creation):

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_MOUSEDOWN</td><td>Mouse button pressed. Event data contains mouse button code.</td></tr><tr><td>  EVENT_MOUSEUP</td><td>Mouse button released. Event data contains mouse button code.</td></tr><tr><td>  EVENT_MOUSEMOVE</td><td>Mouse moved. Event x and y contain mouse coordinates.</td></tr><tr><td>  EVENT_MOUSEWHEEL</td><td>Mouse wheel spun. Event data contains delta clicks.</td></tr><tr><td>  EVENT_MOUSEENTER</td><td>Mouse entered gadget area.</td></tr><tr><td>  EVENT_MOUSELEAVE</td><td>Mouse left gadget area.</td></tr><tr><td>  EVENT_KEYDOWN</td><td>Key pressed. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYUP</td><td>Key released. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYCHAR</td><td>Key character. Event data contains unicode value.</table>


<i>Note: The PANEL_SUNKEN / PANEL_RAISED style flags cannot be used with PANEL_GROUP.</i>

See Also: [SetPanelColor](../../maxgui/maxgui.maxgui/#function-setpanelcolor-panel-tgadget-r-g-b) and [SetPanelPixmap](../../maxgui/maxgui.maxgui/#function-setpanelpixmap-panel-tgadget-pixmap-tpixmap-flags-panelpixmap-tile).


#### Example
```blitzmax
' createpanel.bmx

Strict

Import MaxGui.Drivers

AppTitle = "Panel Example"

Local window:TGadget = CreateWindow( AppTitle, 100, 100, 440, 240, Null, WINDOW_TITLEBAR|WINDOW_CLIENTCOORDS|WINDOW_RESIZABLE )

' create an active panel that occupies entire window client area

Local panel:TGadget = CreatePanel(0,0,ClientWidth(window),ClientHeight(window),window,PANEL_ACTIVE)
SetGadgetLayout panel, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED

' and add to it a smaller green panel with a sunken edge

Local panel2:TGadget = CreatePanel(10,10,200,200,panel,PANEL_ACTIVE|PANEL_SUNKEN)
SetGadgetColor(panel2,160,255,160)

' and finally a group panel with a child button

Local group:TGadget = CreatePanel(220,10,200,200,panel,PANEL_GROUP,"Group Label")
Local button:TGadget = CreateButton("Push Button",0,10,ClientWidth(group)-20,26,group)


Repeat
	WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE
			End
	End Select
Forever
```
<br/>

### `Function SetPanelColor( panel:TGadget,r,g,b )`

Set the color of a Panel.

This function has been superseded by [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true), but is available for backwards compatability.
See Also: [CreatePanel](../../maxgui/maxgui.maxgui/#function-createpanel-tgadget-x-y-w-h-group-tgadget-style-0-title) and [SetPanelPixmap](../../maxgui/maxgui.maxgui/#function-setpanelpixmap-panel-tgadget-pixmap-tpixmap-flags-panelpixmap-tile)


<br/>

### `Function SetPanelPixmap( panel:TGadget,pixmap:TPixmap,flags=PANELPIXMAP_TILE)`

Set panel's background image to a pixmap.

This function has been superseded by [SetGadgetPixmap](../../maxgui/maxgui.maxgui/#function-setgadgetpixmap-gadget-tgadget-pixmap-tpixmap-flags-gadgetpixmap-icon), but is available for backwards compatability.

<table><tr><td> <b>Flags</b></td><td><b>Description</b></td></tr><tr><td>  PANELPIXMAP_TILE</td><td>The panel is filled with repeating tiles.</td></tr><tr><td>  PANELPIXMAP_CENTER</td><td>The pixmap is positioned at the center of the panel.</td></tr><tr><td>  PANELPIXMAP_FIT</td><td>The pixmap is scaled to best fit the panel size.</td></tr><tr><td>  PANELPIXMAP_FIT2</td><td>A variant of PANELPIXMAP_FIT where clipping can occur to achieve a better fit.</td></tr><tr><td>  PANELPIXMAP_STRETCH</td><td>The pixmap is stretched to fit the entire panel.</table>


The function can be passed 'Null' as the parameter for <b>pixmap</b>, in which case the pixmap should be removed.

See Also: [CreatePanel](../../maxgui/maxgui.maxgui/#function-createpanel-tgadget-x-y-w-h-group-tgadget-style-0-title) and [SetPanelColor](../../maxgui/maxgui.maxgui/#function-setpanelcolor-panel-tgadget-r-g-b)


<br/>

### `Function CreateTextField:TGadget(x,y,w,h,group:TGadget,style=0)`

Create a TextField gadget.

A TextField is a single line text entry gadget and currently has only one style flag:

<table><tr><td> <b>Flags</b></td><td><b>Description</b></td></tr><tr><td>  TEXTFIELD_PASSWORD</td><td>Masks characters being typed as a string as asterisks.</table>


Irrespective of the flag used, the TextField gadget will emit the following event(s):

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETACTION</td><td>The user has edited the text in the TextField.</table>


It is also possible to validate any typed input before it reaches the TextArea using
the [SetGadgetFilter](../../maxgui/maxgui.maxgui/#function-setgadgetfilter-gadget-tgadget-callback-event-tevent-context-object-context-object-null) command.

See Also: [GadgetText](../../maxgui/maxgui.maxgui/#function-gadgettext-gadget-tgadget), [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), [SetGadgetFilter](../../maxgui/maxgui.maxgui/#function-setgadgetfilter-gadget-tgadget-callback-event-tevent-context-object-context-object-null).


#### Example
```blitzmax
' createtextfield.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Local textfield:TGadget
Local button:TGadget

window=CreateWindow("My Window",30,20,320,200)

textfield=CreateTextField(4,4,120,22,window)
SetGadgetText( textfield,"A textfield gadget" )

' we need an OK button to catch return key

button=CreateButton("OK",130,4,80,24,window,BUTTON_OK)

ActivateGadget textfield

While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
	Case EVENT_GADGETACTION
		Select EventSource()
			Case textfield
				Print "textfield updated"
			Case button
				Print "return key / OK button pressed"
		End Select
	Case EVENT_WINDOWCLOSE
		End
	End Select
Wend
```
<br/>

### `Function TextFieldText$( textfield:TGadget )`

Get the current text in a TextField gadget.

This function has been superseded by [GadgetText](../../maxgui/maxgui.maxgui/#function-gadgettext-gadget-tgadget), but is available for backwards compatability.
See Also: [CreateTextField](../../maxgui/maxgui.maxgui/#function-createtextfield-tgadget-x-y-w-h-group-tgadget-style-0) and [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text)


<br/>

### `Function CreateTextArea:TGadget(x,y,w,h,group:TGadget,style=0)`

Create a TextArea gadget.


A TextArea gadget is a multiline text editor with commands that allow control
over the contents, style and selection of the text it contains.

A TextArea gadget may have the following optional styles:

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  TEXTAREA_WORDWRAP</td><td>Long lines of text 'wrap round' onto the next lines.</td></tr><tr><td>  TEXTAREA_READONLY</td><td>The text cannot be edited by the user.</table>


A TextArea gadget can generate the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETACTION</td><td>The user has modified the text in a TextArea.</td></tr><tr><td>  EVENT_GADGETSELECT</td><td>The text-cursor has moved or a selection of text is made by the user.</td></tr><tr><td>  EVENT_GADGETMENU</td><td>The user has right-clicked somewhere in the TextArea.</table>


It is also possible to validate any typed input before it reaches the TextArea using
the [SetGadgetFilter](../../maxgui/maxgui.maxgui/#function-setgadgetfilter-gadget-tgadget-callback-event-tevent-context-object-context-object-null) command.

See Also: [SetTextAreaText](../../maxgui/maxgui.maxgui/#function-settextareatext-textarea-tgadget-text-pos-0-length-textarea-all-units-textarea-chars), [AddTextAreaText](../../maxgui/maxgui.maxgui/#function-addtextareatext-textarea-tgadget-text), [TextAreaText](../../maxgui/maxgui.maxgui/#function-textareatext-textarea-tgadget-pos-0-length-textarea-all-units-textarea-chars), [TextAreaLen](../../maxgui/maxgui.maxgui/#function-textarealen-textarea-tgadget-units-textarea-chars), [LockTextArea](../../maxgui/maxgui.maxgui/#function-locktextarea-textarea-tgadget),
[UnlockTextArea](../../maxgui/maxgui.maxgui/#function-unlocktextarea-textarea-tgadget), [SetTextAreaTabs](../../maxgui/maxgui.maxgui/#function-settextareatabs-textarea-tgadget-tabwidth), [SetGadgetFont](../../maxgui/maxgui.maxgui/#function-setgadgetfont-gadget-tgadget-font-tguifont-applytochildren-int-false), [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true), [TextAreaCursor](../../maxgui/maxgui.maxgui/#function-textareacursor-textarea-tgadget-units-textarea-chars),
[TextAreaSelLen](../../maxgui/maxgui.maxgui/#function-textareasellen-textarea-tgadget-units-textarea-chars), [FormatTextAreaText](../../maxgui/maxgui.maxgui/#function-formattextareatext-textarea-tgadget-r-g-b-flags-pos-0-length-textarea-all-units-textarea-chars), [SelectTextAreaText](../../maxgui/maxgui.maxgui/#function-selecttextareatext-textarea-tgadget-pos-0-length-textarea-all-units-textarea-chars), [TextAreaChar](../../maxgui/maxgui.maxgui/#function-textareachar-textarea-tgadget-line), [TextAreaLine](../../maxgui/maxgui.maxgui/#function-textarealine-textarea-tgadget-index),
[TextAreaCharX](../../maxgui/maxgui.maxgui/#function-textareacharx-textarea-tgadget-char) and [TextAreaCharY](../../maxgui/maxgui.maxgui/#function-textareachary-textarea-tgadget-char).


#### Example
```blitzmax
' createtextarea.bmx

Import MaxGui.Drivers

Strict 

Global window:TGadget = CreateWindow( "My Window", 130, 20, 400, 400 )

Global textarea:TGadget = CreateTextArea( 0, 0, ClientWidth(window), ClientHeight(window), window )
	SetGadgetLayout( textarea, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED )
	SetGadgetText( textarea, "A TextArea gadget. :-)nnOne line...n...and then another!")
	ActivateGadget( textarea )

' Select the entire third (index: 2 [base-0]) line.
SelectTextAreaText( textarea, 2, 1, TEXTAREA_LINES )

' Output the properties of the current text selection (should be 1, 1 as set above).
Print "TextAreaCursor(): " + TextAreaCursor( textarea, TEXTAREA_LINES )
Print "TextAreaSelLen(): " + TextAreaSelLen( textarea, TEXTAREA_LINES )

While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
		Case EVENT_APPTERMINATE
			End
	End Select
Wend
```
<br/>

### `Function SetTextAreaText( textarea:TGadget,Text$,pos=0,length=TEXTAREA_ALL,units=TEXTAREA_CHARS )`

Set the contents of a TextArea gadget.


See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0), [AddTextAreaText](../../maxgui/maxgui.maxgui/#function-addtextareatext-textarea-tgadget-text) and [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text)


<br/>

### `Function AddTextAreaText( textarea:TGadget,Text$ )`

Append text to the contents of a TextArea gadget.


See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0), [SetTextAreaText](../../maxgui/maxgui.maxgui/#function-settextareatext-textarea-tgadget-text-pos-0-length-textarea-all-units-textarea-chars) and [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text)


<br/>

### `Function TextAreaText$( textarea:TGadget,pos=0,length=TEXTAREA_ALL,units=TEXTAREA_CHARS )`

Get the contents of a TextArea gadget.


See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0), [AddTextAreaText](../../maxgui/maxgui.maxgui/#function-addtextareatext-textarea-tgadget-text), [SetTextAreaText](../../maxgui/maxgui.maxgui/#function-settextareatext-textarea-tgadget-text-pos-0-length-textarea-all-units-textarea-chars) and [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text)


<br/>

### `Function TextAreaLen( textarea:TGadget,units=TEXTAREA_CHARS )`

Get the number of characters in a TextArea gadget.


See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function LockTextArea( textarea:TGadget )`

Lock a TextArea gadget for improved performance when formatting.


See Also: [UnlockTextArea](../../maxgui/maxgui.maxgui/#function-unlocktextarea-textarea-tgadget) and [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function UnlockTextArea( textarea:TGadget )`

Unlock a previously locked TextArea gadget.


See Also: [LockTextArea](../../maxgui/maxgui.maxgui/#function-locktextarea-textarea-tgadget) and [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function SetTextAreaTabs( textarea:TGadget,tabwidth )`

Set the tab stops of a TextArea gadget measured in pixels.


See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0) SetIndents


<br/>

### `Function SetMargins( textarea:TGadget,leftmargin )`

Set left margin of a TextArea measured in pixels.


See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0) and [SetTextAreaTabs](../../maxgui/maxgui.maxgui/#function-settextareatabs-textarea-tgadget-tabwidth)


<br/>

### `Function SetTextAreaFont( textarea:TGadget,font:TGuiFont )`

Set the font of a TextArea gadget.

This function has been superseded by [SetGadgetFont](../../maxgui/maxgui.maxgui/#function-setgadgetfont-gadget-tgadget-font-tguifont-applytochildren-int-false), but is available for backwards compatability.
See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function SetTextAreaColor( textarea:TGadget,r,g,b,bg=False )`

Set the background or foreground colors of a TextArea gadget.

This function has been superseded by [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true), but is available for backwards compatability.
See Also: [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function TextAreaCursor( textarea:TGadget,units=TEXTAREA_CHARS )`

Find the position of the cursor in a TextArea gadget.


Use the default TEXTAREA_CHARS units argument to find out which character
(column) in the line the cursor is on and use TEXTAREA_LINES to find out
which line (row) the cursor is on.

See Also: [TextAreaSelLen](../../maxgui/maxgui.maxgui/#function-textareasellen-textarea-tgadget-units-textarea-chars) and [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function TextAreaSelLen( textarea:TGadget,units=TEXTAREA_CHARS )`

Find the size of the selected text in a TextArea gadget.


The TEXTAREA_CHARS option returns the number of characters currently
highlighted by the user where as TEXTAREA_LINES will specify the
function returns the number of lines selected.

See Also: [TextAreaCursor](../../maxgui/maxgui.maxgui/#function-textareacursor-textarea-tgadget-units-textarea-chars) and [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function FormatTextAreaText( textarea:TGadget,r,g,b,flags,pos=0,length=TEXTAREA_ALL,units=TEXTAREA_CHARS )`

Format the color and style of some text in a TextArea gadget.


The <b>r</b>, <b>g</b> and <b>b</b> parameters represent the <b>r</b>ed, <b>g</b>reen and <b>b</b>lue components (0..255)
which, when combined, represent the new text color for the the sepecified region
of characters.

The <b>flags</b> parameter can be a combination of the following values:

<table><tr><td> <b>Constant</b></td><td><b>Meaning</b></td></tr><tr><td>  TEXTFORMAT_BOLD</td><td>Bold</td></tr><tr><td>  TEXTFORMAT_ITALIC</td><td>Italic</td></tr><tr><td>  TEXTFORMAT_UNDERLINE</td><td>Underline</td></tr><tr><td>  TEXTFORMAT_STRIKETHROUGH</td><td>StrikeThrough</table>


Depending on the value of the units parameter the position and length parameters specify
the character position and number of characters or the starting line and the number
of lines that FormatTextAreaText will modify.

See Also: [LockTextArea](../../maxgui/maxgui.maxgui/#function-locktextarea-textarea-tgadget) and [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function SelectTextAreaText( textarea:TGadget,pos=0,length=TEXTAREA_ALL,units=TEXTAREA_CHARS )`

Select a range of text in a TextArea gadget.


Depending on the value of the units the position and length parameters specify
the character position and number of characters or the starting line and the number
of lines that SelextTextAreaText will highlight.

See Also: [TextAreaCursor](../../maxgui/maxgui.maxgui/#function-textareacursor-textarea-tgadget-units-textarea-chars), [TextAreaSelLen](../../maxgui/maxgui.maxgui/#function-textareasellen-textarea-tgadget-units-textarea-chars) and [CreateTextArea](../../maxgui/maxgui.maxgui/#function-createtextarea-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function TextAreaChar( textarea:TGadget,Line )`

Find the character position of a given line in a TextArea gadget.

<br/>

### `Function TextAreaLine( textarea:TGadget,index )`

Find the line of a given character position in a TextArea gadget.

<br/>

### `Function TextAreaCharX( textarea:TGadget, char )`

Find the x-coordinate of a textarea character position, relative to the upper left corner of the gadget.

The returned value may be greater than the width of the gadget (or even negative) if the specified character
index is positioned outside the immediately visible area of a scrollable TextArea.


<br/>

### `Function TextAreaCharY( textarea:TGadget, char )`

Find the y-coordinate of a textarea character position, relative to the upper left corner of the gadget.

The returned value may be greater than the height of the gadget (or even negative) if the specified character
index is positioned outside the immediately visible area of a scrollable TextArea.


<br/>

### `Function SetTextAreaCaretWidth( textarea:TGadget, width:Int )`

Sets the caret width in a TextArea gadget.




<br/>

### `Function SetTextAreaCaretColor( textarea:TGadget, r:Int, g:Int, b:Int )`

Sets the caret color in a TextArea gadget.




<br/>

### `Function TextAreaHasUndoRedo:Int(textarea:TGadget)`

The TextArea gadget provides its own Undo/Redo facility.




<br/>

### `Function TextAreaEnableUndoRedo(textarea:TGadget, enable:Int)`

Enables or disables undo/redo actions for the specified TextArea gadget.




<br/>

### `Function TextAreaUndoRedoEnabled:Int(textarea:TGadget)`

Returns whether undo/redo actions for the specified TextArea gadget are enabled.




<br/>

### `Function TextAreaUndo(textarea:TGadget)`

Performs an undo action for the given TextArea gadget.




<br/>

### `Function TextAreaRedo(textarea:TGadget)`

Performs a redo action for the given TextArea gadget.




<br/>

### `Function TextAreaCanUndo:Int(textarea:TGadget)`

Returns [True](../../brl/brl.blitz/#true) if the TextArea can perform an undo action.




<br/>

### `Function TextAreaCanRedo:Int(textarea:TGadget)`

Returns [True](../../brl/brl.blitz/#true) if the TextArea can perform a redo action.




<br/>

### `Function TextAreaClearUndoRedo(textarea:TGadget)`

Clears any cached undo/redo actions for the TextArea.




<br/>

### `Function CreateComboBox:TGadget(x,y,w,h,group:TGadget,style=0)`

Create a ComboBox gadget.


A ComboBox gadget provides a dropdown list of items to the user.

The ComboBox supports the following styles:

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  COMBOBOX_EDITABLE</td><td>Allows the ComboBox to behave similar to a TextField, by allowing typed user input also.</table>


And emits the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETACTION</td><td>The selection has been cleared, or the text has changed.</table>


See Also: [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null), [ClearGadgetItems](../../maxgui/maxgui.maxgui/#function-cleargadgetitems-gadget-tgadget), [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index),
[RemoveGadgetItem](../../maxgui/maxgui.maxgui/#function-removegadgetitem-gadget-tgadget-index), [SelectedGadgetItem](../../maxgui/maxgui.maxgui/#function-selectedgadgetitem-gadget-tgadget) and [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip).


#### Example
```blitzmax
' createcombobox.bmx

Strict

Import MaxGui.Drivers

AppTitle = "ComboBox Style Example"

Global window:TGadget = CreateWindow( AppTitle, 100, 100, 300, 200, Null, WINDOW_TITLEBAR|WINDOW_STATUS )
	
	CreateLabel( "No Style (0): ", 5, 5, ClientWidth(window)-10, 24, window, LABEL_LEFT )
	Global stdComboBox:TGadget = CreateComboBox( 5, 29, ClientWidth(window)-10, 26, window, 0 )
		AddGadgetItem stdComboBox, "Short"
		AddGadgetItem stdComboBox, "Medium"
		AddGadgetItem stdComboBox, "Fat", True
		AddGadgetItem stdComboBox, "Humungous"
		
	CreateLabel( "COMBOBOX_EDITABLE: ", 5, 59, ClientWidth(window)-10, 24, window, LABEL_LEFT )
	Global editcombobox:TGadget = CreateComboBox( 5, 83, ClientWidth(window)-10, 26, window, COMBOBOX_EDITABLE )
		AddGadgetItem editcombobox, "United Kingdom"
		AddGadgetItem editcombobox, "United States", True

Local tmpText$

Repeat
	WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		'Combobox Event(s)
		'EventData() holds the index of the selected item (or -1 if no item is currently selected)
		Case EVENT_GADGETACTION
			Select EventSource()
				Case stdComboBox
					tmpText = ""
					If EventData() > -1 Then
						tmpText = GadgetItemText(TGadget(EventSource()), EventData())
					EndIf
					SetStatusText window, "Weight chosen: " + tmpText
				Case editComboBox
					tmpText = ""
					If EventData() > -1 Then 
						tmpText = GadgetItemText(TGadget(EventSource()), EventData())
					Else 
						tmpText = GadgetText(TGadget(EventSource())) + " [user text]"
					EndIf
					SetStatusText window, "Country chosen: " + tmpText
			EndSelect
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE
			End
	EndSelect
Forever
```
<br/>

### `Function CreateListBox:TGadget(x,y,w,h,group:TGadget,style=0)`

Create a ListBox gadget.


A ListBox gadget displays a scrollable list of items and generates the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETSELECT</td><td>An item has been selected, or the selection has been cleared.</td></tr><tr><td>  EVENT_GADGETACTION</td><td>An item has been double-clicked.</td></tr><tr><td>  EVENT_GADGETMENU</td><td>The user has right-clicked somewhere in the listbox.</table>


See Also: [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null), [ClearGadgetItems](../../maxgui/maxgui.maxgui/#function-cleargadgetitems-gadget-tgadget), [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index),
[RemoveGadgetItem](../../maxgui/maxgui.maxgui/#function-removegadgetitem-gadget-tgadget-index), [SelectedGadgetItem](../../maxgui/maxgui.maxgui/#function-selectedgadgetitem-gadget-tgadget), [SelectedGadgetItems](../../maxgui/maxgui.maxgui/#function-selectedgadgetitems-gadget-tgadget) and [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip).


#### Example
```blitzmax
' createlistbox.bmx

Strict

Import MaxGui.Drivers

AppTitle = "ListBox Example"

Global window:TGadget = CreateWindow( AppTitle, 100, 100, 200, 200, Null, WINDOW_TITLEBAR|WINDOW_STATUS|WINDOW_RESIZABLE )
	
	Global listbox:TGadget = CreateListBox( 0, 0, ClientWidth(window), ClientHeight(window), window )
	SetGadgetLayout listbox, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED
	
	SetGadgetIconStrip listbox, LoadIconStrip("toolbar.png")
	AddGadgetItem listbox, "New", False, 0, "Create something."
	AddGadgetItem listbox, "Open", False, 1, "Open something."
	AddGadgetItem listbox, "Save", False, 2, "Save something.", "Extra Item Object!"
	AddGadgetItem listbox, "No Icon", False, -1, "This should not have an icon set."
	

SelectGadgetItem listbox, 2

While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE;End
		'ListBox Event(s)
		'EventData() holds the index of the corresponding listbox item.
		Case EVENT_GADGETSELECT
			SetStatusText window, "Selected Item Index: " + EventData()
		Case EVENT_GADGETACTION
			SetStatusText window, "Double-Clicked Item Index: " + EventData()
		Case EVENT_GADGETMENU
			SetStatusText window, "Right-Clicked Item Index: " + EventData()
	End Select
Wend
```
<br/>

### `Function CreateTabber:TGadget(x,y,w,h,group:TGadget,style=0)`

Create a Tabber gadget.


A Tabber gadget shows a list of tabs above a client area, typically used for
handling multiple documents/panels.

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETACTION</td><td>A new tab has been selected. Event data contains the tab index.</td></tr><tr><td>  EVENT_GADGETMENU</td><td>A tab has been right-clicked. Event data contains the tab index.</table>


Event extra for both events point to the [GadgetItemExtra](../../maxgui/maxgui.maxgui/#function-gadgetitemextra-object-gadget-tgadget-index) object set for the corresponding tab item index in the latest call
to [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null) / [InsertGadgetItem](../../maxgui/maxgui.maxgui/#function-insertgadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null) or [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null).

It is important to note also that, similar to [SelectedGadgetItem](../../maxgui/maxgui.maxgui/#function-selectedgadgetitem-gadget-tgadget), either event may be emitted with the event
data set to '-1'. This either means that somehow the user has deselected a tab, or that the user
has right-clicked on an area of the tabber which doesn't represent a particular tab item index. As
such, your MaxGUI applications should check the value before proceeding to use it with any of the
standard [GadgetItemText](../../maxgui/maxgui.maxgui/#function-gadgetitemtext-gadget-tgadget-index), [GadgetItemExtra](../../maxgui/maxgui.maxgui/#function-gadgetitemextra-object-gadget-tgadget-index) etc. commands.

See Also: [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null), [ClearGadgetItems](../../maxgui/maxgui.maxgui/#function-cleargadgetitems-gadget-tgadget), [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index),
[RemoveGadgetItem](../../maxgui/maxgui.maxgui/#function-removegadgetitem-gadget-tgadget-index), [SelectedGadgetItem](../../maxgui/maxgui.maxgui/#function-selectedgadgetitem-gadget-tgadget) and [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip).


#### Example
```blitzmax
' createtabber.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Local tabber:TGadget
Local document:TGadget[3]
Local currentdocument:TGadget

' CreateDocument creates a hidden panel that fills entire tabber client area 

Function CreateDocument:TGadget(tabber:TGadget)
	Local	panel:TGadget
	panel=CreatePanel(0,0,ClientWidth(tabber),ClientHeight(tabber),tabber)
	SetGadgetLayout panel,1,1,1,1
	HideGadget panel
	Return panel
End Function

' create a default window with a tabber gadget that fills entire client area

window=CreateWindow("My Window",30,20,400,300)

tabber=CreateTabber(0,0,ClientWidth(window),ClientHeight(window),window)
SetGadgetLayout tabber,1,1,1,1 

' add three items and corresponding document panels to the tabber

AddGadgetItem tabber,"Document 0 R",False,-1,""
AddGadgetItem tabber,"Document 1 G",False,-1,"Tabber Tip 1"
AddGadgetItem tabber,"Document 2 B",False,-1,"tips 4 2"

document[0]=CreateDocument(tabber)
document[1]=CreateDocument(tabber)
document[2]=CreateDocument(tabber)

SetPanelColor document[0],255,200,200
SetPanelColor document[1],200,255,200
SetPanelColor document[2],200,200,255

' our documents start off hidden so make first one current and show

currentdocument=document[0]
ShowGadget currentdocument

' standard message loop with special tabber EVENT_GADGETACTION and EVENT_GADGETMENU handling

While WaitEvent()
	Select EventID()
		Case EVENT_GADGETACTION
			If EventSource()=tabber
				HideGadget currentdocument
				currentdocument=document[EventData()]
				ShowGadget currentdocument
			EndIf
		Case EVENT_GADGETMENU
			If EventSource()=tabber
				Notify "You right clicked the tab with index " + EventData() + "!"
			EndIf
		Case EVENT_WINDOWCLOSE
			End
	End Select
Wend
```
<br/>

### `Function ClearGadgetItems(gadget:TGadget)`

Remove all items added to a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function AddGadgetItem(gadget:TGadget,Text$,flags=0,icon=-1,tip$="",extra:Object=Null)`

Add an item to a list based gadget.


An item can be added to the ComboBox, ListBox, Tabber and Toolbar list based gadgets.

Its <b>text</b> parameter is used as its label.

The <b>flags</b> parameter can be a combination of the following values:

<table><tr><td> <b>Flag</b></td><td><b>Meaning</b></td></tr><tr><td>  GADGETITEM_NORMAL</td><td>A plain gadget item.</td></tr><tr><td>  GADGETITEM_DEFAULT</td><td>The item defaults to a selected state.</td></tr><tr><td>  GADGETITEM_TOGGLE</td><td>The item alternates between selected states when pressed.</td></tr><tr><td>  GADGETITEM_LOCALIZED</td><td>The item text and tooltip are localization strings.</table>


The <b>tip</b>$ parameter attaches an optional tooltip to the item.

The optional <b>icon</b> parameter specifies an icon from the gadget's IconStrip (see [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip)).

The <b>extra</b> parameter is supplied in the EventExtra field of any Event generated by the Item.

See Also: [InsertGadgetItem](../../maxgui/maxgui.maxgui/#function-insertgadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip).


<br/>

### `Function InsertGadgetItem(gadget:TGadget,index,Text$,flags=0,icon=-1,tip$="",extra:Object=Null)`

Inserts an item in a list based gadget at the specified index.


An item can be inserted in a ComboBox, ListBox, Tabber and Toolbar list based gadgets.

See [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null) for a description of the parameters.

See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0) and [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function ModifyGadgetItem( gadget:TGadget,index,Text$,flags=0,icon=-1,tip$="",extra:Object=Null )`

Modify the properties of a gadget-item.


See [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null) for a description of the parameters.

See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0) and [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function RemoveGadgetItem( gadget:TGadget,index )`

Remove a gadget-item from a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0) and [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function EnableGadgetItem( gadget:TGadget,index )`

Enable a particular item in a list based gadget.

Typically, this can only be used on toolbars.
See Also: [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function DisableGadgetItem( gadget:TGadget,index )`

Disable a particular item in a list based gadget.

Typically, this can only be used on toolbars.
See Also: [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function SelectGadgetItem(gadget:TGadget,index)`

Select an item in a list based gadget.


See Also: [DeselectGadgetItem](../../maxgui/maxgui.maxgui/#function-deselectgadgetitem-gadget-tgadget-index), [ToggleGadgetItem](../../maxgui/maxgui.maxgui/#function-togglegadgetitem-gadget-tgadget-index), [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function DeselectGadgetItem(gadget:TGadget,index)`

Deselect an item in a list based gadget.


See Also: [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index), [ToggleGadgetItem](../../maxgui/maxgui.maxgui/#function-togglegadgetitem-gadget-tgadget-index), [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function ToggleGadgetItem(gadget:TGadget,index)`

Invert the selected state of an item in a list based gadget.


See Also: [SelectGadgetItem](../../maxgui/maxgui.maxgui/#function-selectgadgetitem-gadget-tgadget-index), [DeselectGadgetItem](../../maxgui/maxgui.maxgui/#function-deselectgadgetitem-gadget-tgadget-index) and [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function SelectedGadgetItem(gadget:TGadget)`

Get the index of the first selected item in a list based gadget.


SelectedGadgetItem will return -1 if the list based gadget has no selected items.

See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function SelectedGadgetItems[](gadget:TGadget)`

Returns an integer array of the selected item indexes in a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function CountGadgetItems( gadget:TGadget )`

Get the number of items in a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0) and [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function GadgetItemText$( gadget:TGadget,index )`

Get the text of a given item in a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function GadgetItemTooltip$( gadget:TGadget,index )`

Get the tooltip of a given item in a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function GadgetItemIcon( gadget:TGadget,index )`

Get the icon of a given item in a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function GadgetItemExtra:Object( gadget:TGadget,index )`

Get the extra data of a given item in a list based gadget.


See Also: [CreateComboBox](../../maxgui/maxgui.maxgui/#function-createcombobox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateListBox](../../maxgui/maxgui.maxgui/#function-createlistbox-tgadget-x-y-w-h-group-tgadget-style-0), [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0) and [CreateTabber](../../maxgui/maxgui.maxgui/#function-createtabber-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function GadgetItemFlags( gadget:TGadget,index )`

Get the flags parameter of a given item in a list based gadget.


See Also: [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null)


<br/>

### `Function CreateToolBar:TGadget(source:Object,x,y,w,h,window:TGadget,style=0)`

Creates a window toolbar.


A Toolbar is created from an iconstrip - an image that contains a row of equally shaped icons.
Any images in the row left blank are treated as Toolbar separators.

Toolbars are positioned along the top of the <b>window</b> and either the client-area and/or window frame will be
resized so that the client area of the window will begin just below the toolbar.

At present, MaxGUI windows only support one toolbar at a time.

A Toolbar generates the following events:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETACTION</td><td>A toolbar item has been selected/clicked. Event data contains the item index.</table>


The <b>source</b> parameter can be a previously loaded <b>TIconStrip</b>, a [TPixmap](../../brl/brl.pixmap/tpixmap) or a URL to an image
file which <b>CreateToolBar</b> will attempt to load an icon-strip from automatically.

The recommended icon size is 24x24 pixels which seems to work well on most platforms. Using a
different icon size may result in the pixmaps being scaled before being set depending on the OS.

The <b>x</b>, <b>y</b>, <b>w</b>, <b>h</b> parameters are all ignored and are simply there to make the CreateToolbar() system call
consistent with the other <b>CreateGadget()</b> calls.

The toolbar can be alterted during runtime using the [ClearGadgetItems](../../maxgui/maxgui.maxgui/#function-cleargadgetitems-gadget-tgadget), [InsertGadgetItem](../../maxgui/maxgui.maxgui/#function-insertgadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null), [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null) etc.
functions.  Use the GADGETICON_SEPARATOR constant as an item's icon if you want it to be a separator, or
GADGETICON_BLANK if you would like a blank square icon instead.

<i>IMPORTANT: Toolbars should only be parented to window gadgets.  Parenting a toolbar to a panel is not
officially supported - users are strongly advised to instead use push-buttons with pixmap icons set.  Debug builds
will output a warning message to standard error if toolbars are parented otherwise.</i>

See Also: [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null), [EnableGadgetItem](../../maxgui/maxgui.maxgui/#function-enablegadgetitem-gadget-tgadget-index), [DisableGadgetItem](../../maxgui/maxgui.maxgui/#function-disablegadgetitem-gadget-tgadget-index) and [SetToolbarTips](../../maxgui/maxgui.maxgui/#function-settoolbartips-toolbar-tgadget-tips).


#### Example
```blitzmax
' createtoolbar.bmx

Strict

Import MaxGui.Drivers

AppTitle = "ToolBar Example"

Global window:TGadget = CreateWindow( AppTitle, 100, 100, 400, 32, Null, WINDOW_TITLEBAR|WINDOW_STATUS|WINDOW_RESIZABLE|WINDOW_CLIENTCOORDS )

	Global toolbar:TGadget = CreateToolBar( "toolbar.png", 0, 0, 0, 0, window )

	DisableGadgetItem toolbar, 2
	
	SetToolBarTips toolbar, ["New", "Open", "Save should be disabled."] 
	
	AddGadgetItem toolbar, "", 0, GADGETICON_SEPARATOR	'Add a separator.
	AddGadgetItem toolbar, "Toggle", GADGETITEM_TOGGLE, 2, "This toggle button should change to a light bulb when clicked."

	Global button:TGadget = CreateButton( "Show/Hide Toolbar", 2, 2, 180, 28, window )
	SetGadgetLayout button, EDGE_ALIGNED, EDGE_CENTERED, EDGE_ALIGNED, EDGE_CENTERED
	
While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE, EVENT_APPTERMINATE;End
		'ToolBar Event(s)
		'EventData() holds the index of the toolbar item clicked.
		Case EVENT_GADGETACTION
			Select EventSource()
				Case button
					If GadgetHidden(toolbar) Then ShowGadget(toolbar) Else HideGadget(toolbar)
				Case toolbar 
					SetStatusText window, "Toolbar Item Clicked: " + EventData()
			EndSelect
	End Select
Wend
```
<br/>

### `Function SetToolBarTips( toolbar:TGadget,tips$[] )`

Attach a list of tips to a Toolbar gadget.

Simply provides a quick way to set the tooltips of a toolbar's items after them being added.
See Also: [CreateToolbar](../../maxgui/maxgui.maxgui/#function-createtoolbar-tgadget-source-object-x-y-w-h-window-tgadget-style-0)


<br/>

### `Function CreateTreeView:TGadget(x,y,w,h,group:TGadget,style=0)`

Create a TreeView gadget.


A TreeView provides a view of an expandable list of nodes populated with the
[AddTreeViewNode](../../maxgui/maxgui.maxgui/#function-addtreeviewnode-tgadget-text-node-tgadget-icon-1-extra-object-null) command. TreeView nodes can themselves contain nodes providing
a flexible method of displaying a hierachy of information.

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETSELECT</td><td>The user has selected a node.</td></tr><tr><td>  EVENT_GADGETACTION</td><td>The user has double-clicked a node.</td></tr><tr><td>  EVENT_GADGETOPEN</td><td>The user has expanded a node, revealing its children.</td></tr><tr><td>  EVENT_GADGETCLOSE</td><td>The user has collapsed a node, hiding its children.</td></tr><tr><td>  EVENT_GADGETMENU</td><td>The user has right-clicked somewhere in the TreeView.</table>


Each event will have the containing TreeView gadget as the event source and the concerned
node gadget in the EventExtra field of the [TEvent](../../brl/brl.event/tevent).

See Also: [AddTreeViewNode](../../maxgui/maxgui.maxgui/#function-addtreeviewnode-tgadget-text-node-tgadget-icon-1-extra-object-null), [InsertTreeViewNode](../../maxgui/maxgui.maxgui/#function-inserttreeviewnode-tgadget-index-text-node-tgadget-icon-1-extra-object-null), [ModifyTreeViewNode](../../maxgui/maxgui.maxgui/#function-modifytreeviewnode-node-tgadget-text-icon-1), [TreeViewRoot](../../maxgui/maxgui.maxgui/#function-treeviewroot-tgadget-treeview-tgadget),
[SelectedTreeViewNode](../../maxgui/maxgui.maxgui/#function-selectedtreeviewnode-tgadget-treeview-tgadget) and [CountTreeViewNodes](../../maxgui/maxgui.maxgui/#function-counttreeviewnodes-node-tgadget), [SelectTreeViewNode](../../maxgui/maxgui.maxgui/#function-selecttreeviewnode-node-tgadget), [ExpandTreeViewNode](../../maxgui/maxgui.maxgui/#function-expandtreeviewnode-node-tgadget),
[CollapseTreeViewNode](../../maxgui/maxgui.maxgui/#function-collapsetreeviewnode-node-tgadget) and [FreeTreeViewNode](../../maxgui/maxgui.maxgui/#function-freetreeviewnode-node-tgadget).


#### Example
```blitzmax
' createtreeview.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget=CreateWindow("My Window",50,50,240,240,Null,WINDOW_TITLEBAR|WINDOW_CLIENTCOORDS)
Local treeview:TGadget=CreateTreeView(5,5,ClientWidth(window)-10,ClientHeight(window)-10,window)

SetGadgetLayout treeview, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED, EDGE_ALIGNED

Local root:TGadget=TreeViewRoot(treeview)

Local help:TGadget=AddTreeViewNode("Help",root)
AddTreeViewNode "Topic 1",help
AddTreeViewNode "Topic 2",help
AddTreeViewNode "Topic 3",help

Local projects:TGadget=AddTreeViewNode("Projects",root)
AddTreeViewNode("Sub Project",AddTreeViewNode("Project 1",projects))
AddTreeViewNode("Project 2",projects)
AddTreeViewNode("Project 3",projects)

While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
	End Select
Wend
```
<br/>

### `Function AddTreeViewNode:TGadget( Text$,node:TGadget,icon=-1,extra:Object=Null )`

Add a node to a TreeView gadget.

The optional <b>extra</b> parameter is for convenience and is equivalent to calling
[SetGadgetExtra](../../maxgui/maxgui.maxgui/#function-setgadgetextra-gadget-tgadget-extra-object) immediately after the node is created.

See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0), [InsertTreeViewNode](../../maxgui/maxgui.maxgui/#function-inserttreeviewnode-tgadget-index-text-node-tgadget-icon-1-extra-object-null)


<br/>

### `Function InsertTreeViewNode:TGadget( index,Text$,node:TGadget,icon=-1,extra:Object=Null )`

Insert a node at a given index in a TreeView gadget.

The optional <b>extra</b> parameter is for convenience and is equivalent to calling
[SetGadgetExtra](../../maxgui/maxgui.maxgui/#function-setgadgetextra-gadget-tgadget-extra-object) immediately after the node is created.

See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0), [AddTreeViewNode](../../maxgui/maxgui.maxgui/#function-addtreeviewnode-tgadget-text-node-tgadget-icon-1-extra-object-null)


<br/>

### `Function ModifyTreeViewNode( node:TGadget,Text$,icon=-1 )`

Modify a node.


See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function ClearTreeView( treeview:TGadget )`

Frees all the nodes of a TreeView.


See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function TreeViewRoot:TGadget( treeview:TGadget )`

Get the root node of a TreeView gadget.

This is required to parent the first nodes of a blank treeview to.

A treeview's root node can also be used to deselect any currently selected
nodes (see [SelectTreeViewNode](../../maxgui/maxgui.maxgui/#function-selecttreeviewnode-node-tgadget) for more information).

See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function SelectedTreeViewNode:TGadget( treeview:TGadget )`

Get the node currently selected in a TreeView gadget.

Will return [Null](../../brl/brl.blitz/#null) if there aren't any nodes currently selected.

See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0), [SelectTreeViewNode](../../maxgui/maxgui.maxgui/#function-selecttreeviewnode-node-tgadget)


<br/>

### `Function CountTreeViewNodes( node:TGadget )`

Get the number of children of a Node gadget.


See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function SelectTreeViewNode( node:TGadget )`

Selects/highlights a treeview node.

It is possible to deselect a selection by selecting a treeview's root node.
For example:

```
SelectTreeViewNode( TreeViewRoot( myTree ) )
````


See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0), [SelectedTreeViewNode](../../maxgui/maxgui.maxgui/#function-selectedtreeviewnode-tgadget-treeview-tgadget)


<br/>

### `Function ExpandTreeViewNode( node:TGadget )`

Expands a treeview node in a TreeView gadget.


See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0), [CollapseTreeViewNode](../../maxgui/maxgui.maxgui/#function-collapsetreeviewnode-node-tgadget)


<br/>

### `Function CollapseTreeViewNode( node:TGadget )`

Collapses a treeview node in a TreeView gadget.


See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0), [ExpandTreeViewNode](../../maxgui/maxgui.maxgui/#function-expandtreeviewnode-node-tgadget)


<br/>

### `Function FreeTreeViewNode( node:TGadget )`

Removes a treeview node from a TreeView gadget.

This function has been superseded by [FreeGadget](../../maxgui/maxgui.maxgui/#function-freegadget-gadget-tgadget), but is available for backwards compatability.

See Also: [CreateTreeView](../../maxgui/maxgui.maxgui/#function-createtreeview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function CreateHTMLView:TGadget(x,y,w,h,group:TGadget,style=0)`

Create an HTMLView gadget.


The HTMLView is a complete web browser object inside a MaxGUI gadget. The HTML
page displayed is controlled with the [HTMLViewGo](../../maxgui/maxgui.maxgui/#function-htmlviewgo-view-tgadget-url) command or from the user navigating
from within the currently viewed page.

[CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0) supports the following styles:

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  HTMLVIEW_NOCONTEXTMENU</td><td>The webpage's default context menu is disabled.</td></tr><tr><td>  HTMLVIEW_NONAVIGATE</td><td>User navigation is disabled and EVENT_GADGETACTION is generated instead.</table>


<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETDONE</td><td>Generated when a webpage has finished loading or a page anchor has been scrolled to.</td></tr><tr><td>  EVENT_GADGETACTION</td><td>Generated when a user clicks a link. Event Text contains the requested URL.</table>


<i>Note: EVENT_GADGETACTION requires the HTMLVIEW_NONAVIGATE style flag.</i>

See Also: [HtmlViewGo](../../maxgui/maxgui.maxgui/#function-htmlviewgo-view-tgadget-url), [HtmlViewBack](../../maxgui/maxgui.maxgui/#function-htmlviewback-view-tgadget), [HtmlViewForward](../../maxgui/maxgui.maxgui/#function-htmlviewforward-view-tgadget), [HtmlViewStatus](../../maxgui/maxgui.maxgui/#function-htmlviewstatus-view-tgadget) and [HtmlViewCurrentURL](../../maxgui/maxgui.maxgui/#function-htmlviewcurrenturl-view-tgadget).


#### Example
```blitzmax
' createhtmlview.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget
Local htmlview:TGadget

window=CreateWindow("My Window",30,20,600,440,,15|WINDOW_ACCEPTFILES)

htmlview=CreateHTMLView(0,0,ClientWidth(window),ClientHeight(window),window)
SetGadgetLayout htmlview,1,1,1,1 

HtmlViewGo htmlview,"www.blitzmax.com"

While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
	End Select
Wend
```
<br/>

### `Function HtmlViewGo( view:TGadget,url$ )`

Direct the HTMLView gadget to a new URL.


See Also: [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function HtmlViewBack( view:TGadget )`

Go back a page in an HTMLView gadget.


See Also: [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function HtmlViewForward( view:TGadget )`

Go forward a page in an HTMLView gadget.


See Also: [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function HtmlViewStatus( view:TGadget )`

Get the status of an HTMLView gadget.


See Also: [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function HtmlViewCurrentURL$( view:TGadget )`

Get the current URL of an HTMLView gadget.


See Also: [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function HtmlViewRun$( view:TGadget,script$ )`

Run a script in an HTMLView gadget.


See Also: [CreateHTMLView](../../maxgui/maxgui.maxgui/#function-createhtmlview-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function CreateLabel:TGadget( name$,x,y,w,h,group:TGadget,style=LABEL_LEFT )`

Create a Label gadget.


A Label gadget is used to place static text or frames in a MaxGUI user interface. They do not
generate any events.

Labels support these optional styles:

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  LABEL_FRAME</td><td>The label has a simple border.</td></tr><tr><td>  LABEL_SUNKENFRAME</td><td>The label has a sunken border.</td></tr><tr><td>  LABEL_SEPARATOR</td><td>The label is an etched box with no text useful for drawing separators.</td></tr><tr><td>  LABEL_LEFT</td><td>The label's text is left-aligned. This is the default.</td></tr><tr><td>  LABEL_CENTER</td><td>The label's text is center-aligned.</td></tr><tr><td>  LABEL_RIGHT</td><td>The label's text is right-aligned.</table>


See Also: [SetGadgetText](../../maxgui/maxgui.maxgui/#function-setgadgettext-gadget-tgadget-text), [SetGadgetTextColor](../../maxgui/maxgui.maxgui/#function-setgadgettextcolor-gadget-tgadget-r-g-b), [SetGadgetFont](../../maxgui/maxgui.maxgui/#function-setgadgetfont-gadget-tgadget-font-tguifont-applytochildren-int-false) and [SetGadgetColor](../../maxgui/maxgui.maxgui/#function-setgadgetcolor-gadget-tgadget-r-g-b-bg-true).


#### Example
```blitzmax
' createlabel.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget

window=CreateWindow("My Window",30,20,320,480)

CreateLabel("A plain label",10,10,280,52,window)
CreateLabel("A label with LABEL_FRAME",10,80,280,60,window,LABEL_FRAME)
CreateLabel("A label with LABEL_SUNKENFRAME",10,150,280,60,window,LABEL_SUNKENFRAME)
CreateLabel("not applicable",10,220,280,54,window,LABEL_SEPARATOR)

While WaitEvent()<>EVENT_WINDOWCLOSE
Wend
```
<br/>

### `Function CreateSlider:TGadget( x,y,w,h,group:TGadget,style=0 )`

Create a Slider gadget.


A Slider gadget supports the following styles:

<table><tr><td> <b>Style</b></td><td><b>Meaning</b></td></tr><tr><td>  SLIDER_HORIZONTAL</td><td>The slider is moved left and right.</td></tr><tr><td>  SLIDER_VERTICAL</td><td>The  slider is moved up and down.</td></tr><tr><td>  SLIDER_SCROLLBAR</td><td>The slider uses a proportional size knob.</td></tr><tr><td>  SLIDER_TRACKBAR</td><td>The slider uses a fixed size knob.</td></tr><tr><td>  SLIDER_STEPPER</td><td>The slider has no knob, just arrow buttons.</table>


A slider only emits one type of event:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_GADGETACTION</td><td>The user has changed the slider's value. Event Data contains the SliderValue.</table>


See Also: [SetSliderRange](../../maxgui/maxgui.maxgui/#function-setsliderrange-slider-tgadget-range0-range1), [SetSliderValue](../../maxgui/maxgui.maxgui/#function-setslidervalue-slider-tgadget-value) and [SliderValue](../../maxgui/maxgui.maxgui/#function-slidervalue-slider-tgadget)


#### Example
```blitzmax
' createslider.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget=CreateWindow("My Window",0,0,240,240,,WINDOW_TITLEBAR)

Local slider:TGadget[3]

' standard vertical and horizontal scroll bars

slider[0]=CreateSlider(10,10,16,100,window,SLIDER_VERTICAL)
slider[1]=CreateSlider(30,10,100,16,window,SLIDER_HORIZONTAL)

' a horizontal trackbar

slider[2]=CreateSlider(30,30,100,24,window,SLIDER_HORIZONTAL|SLIDER_TRACKBAR)

' a row of vertical trackbars

Local trackbar:TGadget[5]

For Local i=0 To 4
	trackbar[i]=CreateSlider(30+i*20,50,16,60,window,SLIDER_VERTICAL|SLIDER_TRACKBAR)
Next

' a single stepper

Local stepper:TGadget
stepper=CreateSlider(10,120,24,24,window,SLIDER_STEPPER)

SetSliderValue stepper,4
Print SliderValue(stepper)

While WaitEvent()
	Print CurrentEvent.ToString()
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
	End Select
Wend
```
<br/>

### `Function SetSliderRange( slider:TGadget,range0,range1 )`

Set the range of a Slider gadget.

For the default SLIDER_SCROLLBAR style the range0,range1 parameters are treated
as a visible / total ratio which dictates both the size of the knob and it's
maximum value. The default value is 1,10 which displays a Slider with a knob
that occupies 1/10th the area and with a [SliderValue](../../maxgui/maxgui.maxgui/#function-slidervalue-slider-tgadget) range of 0..9.

For the SLIDER_TRACKBAR and SLIDER_STEPPER styles the range0,range1 parameters
are treated as the minimum and maximum [SliderValue](../../maxgui/maxgui.maxgui/#function-slidervalue-slider-tgadget) range inclusive.

See Also: [CreateSlider](../../maxgui/maxgui.maxgui/#function-createslider-tgadget-x-y-w-h-group-tgadget-style-0), [SliderValue](../../maxgui/maxgui.maxgui/#function-slidervalue-slider-tgadget) and [SetSliderValue](../../maxgui/maxgui.maxgui/#function-setslidervalue-slider-tgadget-value)


<br/>

### `Function SetSliderValue( slider:TGadget,value )`

Set the position of a Slider gadget.


See Also: [CreateSlider](../../maxgui/maxgui.maxgui/#function-createslider-tgadget-x-y-w-h-group-tgadget-style-0), [SetSliderRange](../../maxgui/maxgui.maxgui/#function-setsliderrange-slider-tgadget-range0-range1) and [SliderValue](../../maxgui/maxgui.maxgui/#function-slidervalue-slider-tgadget)


<br/>

### `Function SliderValue( slider:TGadget )`

Get the position of a Slider gadget.


See Also: [CreateSlider](../../maxgui/maxgui.maxgui/#function-createslider-tgadget-x-y-w-h-group-tgadget-style-0), [SetSliderRange](../../maxgui/maxgui.maxgui/#function-setsliderrange-slider-tgadget-range0-range1) and [SetSliderValue](../../maxgui/maxgui.maxgui/#function-setslidervalue-slider-tgadget-value)


<br/>

### `Function CreateProgBar:TGadget( x,y,w,h,group:TGadget,style=0 )`

Create a Progress Bar gadget.

Similar to Labels, Progress Bar gadgets do not generate any events themselves.
See Also: [UpdateProgBar](../../maxgui/maxgui.maxgui/#function-updateprogbar-progbar-tgadget-value)


#### Example
```blitzmax
' createprogbar.bmx

Import MaxGui.Drivers

Strict 

Local window:TGadget=CreateWindow("My Window",50,50,240,100,,WINDOW_TITLEBAR)

Local progbar:TGadget=CreateProgBar(10,10,200,20,window)

CreateLabel "Please Wait",10,40,200,20,window

CreateTimer 10

While WaitEvent()
	Select EventID()
		Case EVENT_WINDOWCLOSE
			End
		Case EVENT_TIMERTICK
			Local t=EventData()
			If t=50 End
			UpdateProgBar progbar,t/50.0
	End Select
Wend
```
<br/>

### `Function UpdateProgBar( progbar:TGadget,value# )`

Update the display of a ProgressBar gadget.


See Also: [CreateProgBar](../../maxgui/maxgui.maxgui/#function-createprogbar-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function LoadIconStrip:TIconStrip( source:Object )`

Creates an icon strip from an image file.


An icon strip is a series of small images that can be attached to item-based gadgets.

Icons must be square, and arranged in a single horizontal strip across the source image.

The number of icons in an iconstrip is determined by dividing the image width by its height. For example,
an iconstrip 64 wide by 8 high is assumed to contain 64/8=8 icons.

Once an icon strip has been loaded, it can be attached to item-based gadgets using [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip).

See Also: [SetGadgetIconStrip](../../maxgui/maxgui.maxgui/#function-setgadgeticonstrip-gadget-tgadget-iconstrip-ticonstrip) and [PixmapFromIconStrip](../../maxgui/maxgui.maxgui/#function-pixmapfromiconstrip-tpixmap-iconstrip-ticonstrip-index-1)


<br/>

### `Function SetGadgetIconStrip( gadget:TGadget,iconstrip:TIconStrip )`

Attaches an icon strip to an item-based gadget.

Once attached, icons can be specified when items are added or modified with the [AddGadgetItem](../../maxgui/maxgui.maxgui/#function-addgadgetitem-gadget-tgadget-text-flags-0-icon-1-tip-extra-object-null),
[InsertGadgetItem](../../maxgui/maxgui.maxgui/#function-insertgadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null) and [ModifyGadgetItem](../../maxgui/maxgui.maxgui/#function-modifygadgetitem-gadget-tgadget-index-text-flags-0-icon-1-tip-extra-object-null) commands.

This command may only be used with the <b>ComboBox</b>, <b>ListBox</b>, <b>Tabber</b> and <b>TreeNode</b> gadgets.

<i>Note: It is highly recommended that icon-strips are set before any items are added to a gadget.</i>

See Also: [LoadIconStrip](../../maxgui/maxgui.maxgui/#function-loadiconstrip-ticonstrip-source-object)


<br/>

### `Function PixmapFromIconStrip:TPixmap( iconstrip:TIconStrip, index = -1 )`

Returns a pixmap containing either a copy of the original icon-strip or just the specified icon.

<b>iconstrip</b>: The icon-strip to return a pixmap from.

<b>index</b>: The index (base 0) of the icon to extract. If this is negative, a <i>copy</i> of the
original pixmap used to create the iconstrip is returned.

This function will return [Null](../../brl/brl.blitz/#null) if no iconstrip is passed, or if the icon index is invalid.

See Also: [LoadIconStrip](../../maxgui/maxgui.maxgui/#function-loadiconstrip-ticonstrip-source-object)


<br/>

### `Function CreateCanvas:TGadget( x,y,w,h,group:TGadget,style=0 )`

Create a Canvas gadget.


A Canvas provides a [Graphics](../../brl/brl.graphics/#function-graphics-tgraphics-width-height-depth-0-hertz-60-flags-0) interface for realtime drawing purposes.

Once a Canvas is created, the [CanvasGraphics](../../maxgui/maxgui.maxgui/#function-canvasgraphics-tgraphics-gadget-tgadget)() Function can be used with the
[SetGraphics](../../brl/brl.graphics/#function-setgraphics-g-tgraphics) command to direct Max2D drawing commands to be
drawn directly on the Canvas.

An EVENT_GADGETPAINT event is generated whenever the gadget must be redrawn by either
the system (for instance when it is first shown) or due to the [RedrawGadget](../../maxgui/maxgui.maxgui/#function-redrawgadget-gadget-tgadget) command.

An EVENT_GADGETPAINT handler should always call [SetGraphics](../../brl/brl.graphics/#function-setgraphics-g-tgraphics)
with the canvas's Max2D graphics context to ensure the viewport and similar
properties are in their correct state.

When a Canvas is active using either the [ActivateGadget](../../maxgui/maxgui.maxgui/#function-activategadget-gadget-tgadget) command or clicking
on the Canvas when the application is running, the following events will also
be sent from the Canvas:

<table><tr><td> <b>Event ID</b></td><td><b>Description</b></td></tr><tr><td>  EVENT_MOUSEDOWN</td><td>Mouse button pressed. Event data contains mouse button code.</td></tr><tr><td>  EVENT_MOUSEUP</td><td>Mouse button released. Event data contains mouse button code.</td></tr><tr><td>  EVENT_MOUSEMOVE</td><td>Mouse moved. Event x and y contain mouse coordinates.</td></tr><tr><td>  EVENT_MOUSEWHEEL</td><td>Mouse wheel spun. Event data contains delta clicks.</td></tr><tr><td>  EVENT_MOUSEENTER</td><td>Mouse entered gadget area.</td></tr><tr><td>  EVENT_MOUSELEAVE</td><td>Mouse left gadget area.</td></tr><tr><td>  EVENT_KEYDOWN</td><td>Key pressed. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYUP</td><td>Key released. Event data contains keycode.</td></tr><tr><td>  EVENT_KEYCHAR</td><td>Key character. Event data contains unicode value.</table>


See Also: [ActivateGadget](../../maxgui/maxgui.maxgui/#function-activategadget-gadget-tgadget), [RedrawGadget](../../maxgui/maxgui.maxgui/#function-redrawgadget-gadget-tgadget), [CanvasGraphics](../../maxgui/maxgui.maxgui/#function-canvasgraphics-tgraphics-gadget-tgadget)


#### Example
```blitzmax
' createcanvas.bmx

Import MaxGui.Drivers

Strict 

Global GAME_WIDTH=320
Global GAME_HEIGHT=240

' create a centered window with client size GAME_WIDTH,GAME_HEIGHT

Local wx=(ClientWidth(Desktop())-GAME_WIDTH)/2
Local wy=(ClientHeight(Desktop())-GAME_HEIGHT)/2

Local window:TGadget=CreateWindow("My Canvas",wx,wy,GAME_WIDTH,GAME_HEIGHT,Null,WINDOW_TITLEBAR)'|WINDOW_CLIENTCOORDS)

' create a canvas for our game
Local canvas:TGadget=CreateCanvas(0,0,320,240,window)

' create an update timer

CreateTimer 60

While WaitEvent()
	Select EventID()
		Case EVENT_TIMERTICK
			RedrawGadget canvas

		Case EVENT_GADGETPAINT
			SetGraphics CanvasGraphics(canvas)
			SetOrigin 160,120
			SetLineWidth 5
			Cls
			Local t=MilliSecs()
			DrawLine 0,0,120*Cos(t),120*Sin(t)
			DrawLine 0,0,80*Cos(t/60),80*Sin(t/60)
			Flip

		Case EVENT_MOUSEMOVE
			Print "MOVE!"

		Case EVENT_WINDOWCLOSE
			FreeGadget canvas
			End

		Case EVENT_APPTERMINATE
			End
	End Select
Wend
```
<br/>

### `Function CanvasGraphics:TGraphics( gadget:TGadget )`

Retrieve a Canvas gadget's Graphics context.

The [RedrawGadget](../../maxgui/maxgui.maxgui/#function-redrawgadget-gadget-tgadget) example shows an alternative method for drawing to Canvas
gadgets utilizing the EVENT_GADGETPAINT event.

See Also: [CreateCanvas](../../maxgui/maxgui.maxgui/#function-createcanvas-tgadget-x-y-w-h-group-tgadget-style-0)


<br/>

### `Function QueryGadget:Byte Ptr( gadget:TGadget,queryid )`

Return internal gadget handle.

[QueryGadget](../../maxgui/maxgui.maxgui/#function-querygadget-byte-ptr-gadget-tgadget-queryid) retrieves system handles for use with API specific functions.

<table><tr><td> <b>Constant</b></td><td><b>Return Value</b></td></tr><tr><td>  QUERY_HWND</td><td>A Windows API HWND handle.</td></tr><tr><td>  QUERY_HWND_CLIENT</td><td>A Windows API HWND handle representing a gadget's client area.</td></tr><tr><td>  QUERY_NSVIEW</td><td>A Cocoa NSView handle.</td></tr><tr><td>  QUERY_NSVIEW_CLIENT</td><td>A Cocoa NSView representing a gadget's client area.</td></tr><tr><td>  QUERY_FLWIDGET</td><td>An FL_WIDGET handle.</td></tr><tr><td>  QUERY_FLWIDGET_CLIENT</td><td>An FL_WIDGET handle representing a gadget's client area.</table>



<br/>

### `Function GadgetScaleFactor:Int( gadget:TGadget )`

Returns the gadget scale factor that maps from window coordiantes to the actual device pixels.

On traditional systems this is 1, but on very high density outputs this can be a higher value (often 2).


<br/>

