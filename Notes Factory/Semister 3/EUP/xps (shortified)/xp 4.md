# EUP Experiment 4

## Aim
Designing of Windows Form using custom controls.

## Theory

### **ProgressBar**

**Difference between Classic and Custom Controls:**
- **Classic Controls**: Standard control provided by .NET Framework with predefined appearance and behavior. Limited customization options.
- **Custom Controls**: User-defined controls that extend functionality and appearance of the ProgressBar, allowing more customization.

**Properties:**
- **Value**: Current progress value.
- **Minimum**: Minimum value of the progress.
- **Maximum**: Maximum value of the progress.
- **Step**: Increment value for each step.
- **Style**: Display style (blocks or continuous).

**Events:**
- **ValueChanged**: Triggered when the value changes.
- **Click**: Triggered when the ProgressBar is clicked.
- **Paint**: Triggered when the ProgressBar is repainted.
- **MouseEnter**: Triggered when the mouse pointer enters the ProgressBar.
- **MouseLeave**: Triggered when the mouse pointer leaves the ProgressBar.

### **ListView**

**Difference between Classic and Custom Controls:**
- **Classic Controls**: Provides a simple list interface with predefined item display.
- **Custom Controls**: Allows for advanced customization of item display, sorting, and grouping.

**Properties:**
- **View**: Determines the display mode (details, list, etc.).
- **FullRowSelect**: Specifies if the entire row is selected.
- **Sorting**: Defines the sorting order of items.
- **MultiSelect**: Allows multiple items to be selected.
- **CheckBoxes**: Displays checkboxes next to items.

**Events:**
- **ItemSelectionChanged**: Triggered when the selected item changes.
- **ItemChecked**: Triggered when an item's checkbox state changes.
- **ColumnClick**: Triggered when a column header is clicked.
- **SelectedIndexChanged**: Triggered when the selected index changes.
- **ItemActivate**: Triggered when an item is activated.

### **ImageList**

**Difference between Classic and Custom Controls:**
- **Classic Controls**: Provides a simple way to manage and display images.
- **Custom Controls**: Allows more control over image management, including custom image rendering and image manipulation.

**Properties:**
- **Images**: Collection of images.
- **ImageSize**: Size of each image in the list.
- **ColorDepth**: Color depth of images.
- **TransparentColor**: Color that should be treated as transparent.
- **Tag**: User-defined data associated with the ImageList.

**Events:**
- **None**: ImageList does not have specific events.

### **TreeView**

**Difference between Classic and Custom Controls:**
- **Classic Controls**: Displays hierarchical data in a tree structure with basic customization.
- **Custom Controls**: Offers advanced customization for node appearance, behavior, and interaction.

**Properties:**
- **Nodes**: Collection of TreeNode objects.
- **SelectedNode**: Currently selected node.
- **CheckBoxes**: Display checkboxes next to nodes.
- **ImageList**: Image list for node icons.
- **ShowLines**: Determines if lines are shown connecting nodes.

**Events:**
- **AfterSelect**: Triggered after a node is selected.
- **BeforeExpand**: Triggered before a node is expanded.
- **BeforeCollapse**: Triggered before a node is collapsed.
- **NodeMouseClick**: Triggered when a node is clicked.
- **NodeMouseDoubleClick**: Triggered when a node is double-clicked.

### **MenuStrip and StatusStrip**

**Difference between Classic and Custom Controls:**
- **Classic Controls**: Provides a standard menu and status bar with predefined styles and behavior.
- **Custom Controls**: Allows for extensive customization of menu items and status information display.

**Properties:**
- **MenuStrip**:
  - **Items**: Collection of menu items.
  - **Dock**: Docking position on the form.
  - **RenderMode**: Determines the rendering style.
  - **BackColor**: Background color of the menu strip.
  - **ForeColor**: Foreground color of the menu strip.
- **StatusStrip**:
  - **Items**: Collection of status items.
  - **Dock**: Docking position on the form.
  - **RenderMode**: Determines the rendering style.
  - **BackColor**: Background color of the status strip.
  - **ForeColor**: Foreground color of the status strip.

**Events:**
- **MenuStrip**:
  - **ItemClicked**: Triggered when a menu item is clicked.
  - **ItemAdded**: Triggered when a menu item is added.
  - **ItemRemoved**: Triggered when a menu item is removed.
  - **Paint**: Triggered when the MenuStrip is repainted.
  - **Resize**: Triggered when the MenuStrip is resized.
- **StatusStrip**:
  - **ItemClicked**: Triggered when a status item is clicked.
  - **ItemAdded**: Triggered when a status item is added.
  - **ItemRemoved**: Triggered when a status item is removed.
  - **Paint**: Triggered when the StatusStrip is repainted.
  - **Resize**: Triggered when the StatusStrip is resized.

## Conclusion
 hence we successfully performed Designing of Windows Form using custom controls.