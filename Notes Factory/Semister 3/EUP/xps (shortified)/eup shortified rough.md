xp 2
form 2
```csharp
namespace probz_base
{
    public partial class Form2 : Form
    {
        public Form2()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            // weeeee button code
            /*   if (radioButton1.Checked)
               {
                   this.BackColor = Color.Red;
               }
               if (radioButton2.Checked)
               {
                   this.BackColor = Color.Yellow;
               }
               if (radioButton3.Checked)
               {
                   this.BackColor = Color.Green;
               } */
            this.BackColor = Color.White;
        }

        private void radioButton1_CheckedChanged(object sender, EventArgs e)
        {
            this.BackColor = Color.Red;
        }

        private void radioButton2_CheckedChanged(object sender, EventArgs e)
        {
            this.BackColor = Color.Yellow;
        }

        private void radioButton3_CheckedChanged(object sender, EventArgs e)
        {
            this.BackColor = Color.Green;
        }
    }
}
```

form 1
```csharp

namespace probz_base
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            textBox1.Clear();
            textBox2.Clear();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            groupBox1.Visible = true;
        }

        private void button4_Click(object sender, EventArgs e)
        {
            groupBox1.Visible = false;
        }

        private void button1_Click(object sender, EventArgs e)
        {
            /* if (textBox1.Text == "e" && textBox2.Text == "ee")
             {
                 MessageBox.Show("AYYYY");
             }
             else
             {
                 MessageBox.Show("NAYYYY");
             } */
            this.Hide();
            Form2 f2 = new Form2();
            f2.Show();
        }

        private void label3_Click(object sender, EventArgs e)
        {

        }

        private void button5_Click(object sender, EventArgs e)
        {
            // validation code
            String un, up;
            un = textBox1.Text;
            up = textBox2.Text;
            if (string.IsNullOrEmpty(un))
            {
                MessageBox.Show("Mpty usernameeeee");
                return;
            }
            if (string.IsNullOrEmpty(up))
            {
                MessageBox.Show("Mpty passssword");
                return;
            }
            if (up.Length < 7 || un.Length > 20)
            {
                MessageBox.Show("input min  7 and max 20");
                return;
            }
            if (!up.Any(char.IsUpper))
            {
                MessageBox.Show("use upprcase");
                return;
            }
            if (!up.Any(char.IsLower))
            {
                MessageBox.Show("use lowercase");
                return;
            }
           
        }
    }
}


```