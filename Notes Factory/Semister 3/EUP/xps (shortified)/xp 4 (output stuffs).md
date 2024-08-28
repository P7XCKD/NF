

### `Form1.cs`
```csharp
using System;
using System.Windows.Forms;

namespace Probz
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            InitializeCustomControls();
        }

        private void InitializeCustomControls()
        {
            progressBar1.Value = 50;
            progressBar1.Maximum = 100;
            progressBar1.Style = ProgressBarStyle.Continuous;
            progressBar1.Click += new EventHandler(this.progressBar1_Click);

            listView1.View = View.Details;
            listView1.FullRowSelect = true;
            listView1.Sorting = SortOrder.Ascending;
            listView1.CheckBoxes = true;
            listView1.ItemChecked += new ItemCheckedEventHandler(this.listView1_ItemChecked);

            imageList1.ImageSize = new System.Drawing.Size(32, 32);
            imageList1.ColorDepth = ColorDepth.Depth32Bit;
            imageList1.Images.Add(SystemIcons.Information);

            treeView1.CheckBoxes = true;
            treeView1.ImageList = imageList1;
            treeView1.Nodes.Add("Root Node");
            treeView1.Nodes[0].Nodes.Add("Child Node 1");
            treeView1.Nodes[0].Nodes.Add("Child Node 2");
            treeView1.AfterSelect += new TreeViewEventHandler(this.treeView1_AfterSelect);

            menuStrip1.BackColor = System.Drawing.Color.LightBlue;
            menuStrip1.RenderMode = ToolStripRenderMode.Professional;
            menuStrip1.ItemClicked += new ToolStripItemClickedEventHandler(this.menuStrip1_ItemClicked);

            ToolStripMenuItem fileMenu = new ToolStripMenuItem("File");
            fileMenu.DropDownItems.Add("Exit", null, (s, e) => this.Close());
            menuStrip1.Items.Add(fileMenu);

            statusStrip1.BackColor = System.Drawing.Color.LightGray;
            statusStrip1.RenderMode = ToolStripRenderMode.System;
            statusStrip1.ItemClicked += new ToolStripItemClickedEventHandler(this.statusStrip1_ItemClicked);

            ToolStripStatusLabel statusLabel = new ToolStripStatusLabel("Ready");
            statusStrip1.Items.Add(statusLabel);
        }

        private void progressBar1_Click(object sender, EventArgs e)
        {
            MessageBox.Show("ProgressBar clicked!");
        }

        private void listView1_ItemChecked(object sender, ItemCheckedEventArgs e)
        {
            MessageBox.Show($"Item {e.Item.Text} checked state changed.");
        }

        private void treeView1_AfterSelect(object sender, TreeViewEventArgs e)
        {
            MessageBox.Show($"Selected Node: {e.Node.Text}");
        }

        private void menuStrip1_ItemClicked(object sender, ToolStripItemClickedEventArgs e)
        {
            MessageBox.Show($"Menu item {e.ClickedItem.Text} clicked.");
        }

        private void statusStrip1_ItemClicked(object sender, ToolStripItemClickedEventArgs e)
        {
            MessageBox.Show($"Status item {e.ClickedItem.Text} clicked.");
        }
    }
}
```
IGNORE BELOW PART

### `Form1.Designer.cs`
```csharp
namespace Probz
{
    partial class Form1
    {
        private System.ComponentModel.IContainer components = null;
        private ProgressBar progressBar1;
        private ListView listView1;
        private TreeView treeView1;
        private MenuStrip menuStrip1;
        private StatusStrip statusStrip1;
        private ImageList imageList1;

        protected override void Dispose(bool disposing)
        {
            if (disposing && (components != null))
            {
                components.Dispose();
            }
            base.Dispose(disposing);
        }

        private void InitializeComponent()
        {
            this.components = new System.ComponentModel.Container();
            this.progressBar1 = new ProgressBar();
            this.listView1 = new ListView();
            this.treeView1 = new TreeView();
            this.menuStrip1 = new MenuStrip();
            this.statusStrip1 = new StatusStrip();
            this.imageList1 = new ImageList(this.components);
            this.SuspendLayout();

            this.progressBar1.Dock = DockStyle.Top;
            this.progressBar1.Maximum = 100;
            this.progressBar1.Style = ProgressBarStyle.Continuous;
            this.progressBar1.Value = 50;
            this.progressBar1.Click += new EventHandler(this.progressBar1_Click);

            this.listView1.Dock = DockStyle.Top;
            this.listView1.View = View.Details;
            this.listView1.FullRowSelect = true;
            this.listView1.Sorting = SortOrder.Ascending;
            this.listView1.CheckBoxes = true;
            this.listView1.ItemChecked += new ItemCheckedEventHandler(this.listView1_ItemChecked);
            this.listView1.Columns.Add("Column 1", 100);
            this.listView1.Columns.Add("Column 2", 100);
            this.listView1.Items.Add(new ListViewItem(new[] { "Item 1", "Subitem 1" }));

            this.imageList1.ImageSize = new System.Drawing.Size(32, 32);
            this.imageList1.ColorDepth = ColorDepth.Depth32Bit;
            this.imageList1.Images.Add(SystemIcons.Information);

            this.treeView1.Dock = DockStyle.Left;
            this.treeView1.CheckBoxes = true;
            this.treeView1.ImageList = this.imageList1;
            this.treeView1.Nodes.Add("Root Node");
            this.treeView1.Nodes[0].Nodes.Add("Child Node 1");
            this.treeView1.Nodes[0].Nodes.Add("Child Node 2");
            this.treeView1.AfterSelect += new TreeViewEventHandler(this.treeView1_AfterSelect);

            this.menuStrip1.Dock = DockStyle.Top;
            this.menuStrip1.BackColor = System.Drawing.Color.LightBlue;
            this.menuStrip1.RenderMode = ToolStripRenderMode.Professional;
            this.menuStrip1.ItemClicked += new ToolStripItemClickedEventHandler(this.menuStrip1_ItemClicked);
            ToolStripMenuItem fileMenu = new ToolStripMenuItem("File");
            fileMenu.DropDownItems.Add("Exit", null, (s, e) => this.Close());
            this.menuStrip1.Items.Add(fileMenu);

            this.statusStrip1.Dock = DockStyle.Bottom;
            this.statusStrip1.BackColor = System.Drawing.Color.LightGray;
            this.statusStrip1.RenderMode = ToolStripRenderMode.System;
            this.statusStrip1.ItemClicked += new ToolStripItemClickedEventHandler(this.statusStrip1_ItemClicked);
            ToolStripStatusLabel statusLabel = new ToolStripStatusLabel("Ready");
            this.statusStrip1.Items.Add(statusLabel);

            this.AutoScaleDimensions = new System.Drawing.SizeF(8F, 16F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(800, 450);
            this.Controls.Add(this.treeView1);
            this.Controls.Add(this.listView1);
            this.Controls.Add(this.progressBar1);
            this.Controls.Add(this.menuStrip1);
            this.Controls.Add(this.statusStrip1);
            this.MainMenuStrip = this.menuStrip1;
            this.Text = "Form1";
            this.ResumeLayout(false);
            this.PerformLayout();
        }
    }
}
```

