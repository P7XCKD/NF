
# EUP Experiment 5
> [!attention] OUTDATED, YOU CAN COPY THEORY PART
## Aim
Create a custom dialog box and design an MDI (Multiple Document Interface) application with a menu.

## Theory

**MDI Application Overview:**
MDI applications let users manage multiple documents within a single window, making it easy to switch between different forms or views. This design is ideal for applications requiring simultaneous work on several documents.

**Steps to Design an MDI Application:**
1. **Create a Project:** Start a new Windows Forms Application.
2. **Set MDI Parent Form:** Make the main form an MDI container (`IsMdiContainer` property set to `True`).
3. **Add Menu:** Use a `MenuStrip` to provide options for managing child forms.
4. **Add Child Forms:** Create forms that act as child windows and set their `MdiParent` property to the main form.
5. **Implement Menu Handlers:** Write event handlers to manage child forms.

**Applications of MDI Applications:**
- **Text Editors:** Open and edit multiple documents.
- **Graphic Design Software:** Work on several images simultaneously.
- **IDEs:** Handle multiple files and projects in one interface.

**Example Program:**

```csharp
// MDI Parent Form
public partial class MainForm : Form
{
    public MainForm()
    {
        InitializeComponent();
        this.IsMdiContainer = true;
    }

    private void openChildFormToolStripMenuItem_Click(object sender, EventArgs e)
    {
        ChildForm child = new ChildForm();
        child.MdiParent = this;
        child.Show();
    }
}

// Child Form
public partial class ChildForm : Form
{
    public ChildForm()
    {
        InitializeComponent();
    }
}
```

## Conclusion
hence we successfully Created a custom dialog box and design an MDI (Multiple Document Interface) application with a menu

---