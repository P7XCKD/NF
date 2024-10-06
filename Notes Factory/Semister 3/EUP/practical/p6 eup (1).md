
![image](.attachments/257cacbec3116e395f29c169e50bcd90d2b1a663.png) 
![image](.attachments/2d35d2c676052176a14de0923df84a66aecfa85d.png) 



form2
```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Reflection.Emit;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace PROBZZZZZZ
{
    public partial class Form2 : Form
    {
        int s = 0;
        public Form2()
        {
            InitializeComponent();
        }

        private void button4_Click(object sender, EventArgs e)
        {
            this.Hide();
            Form1 f1 = new Form1();
            f1.Show();
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            s += 1;
            label1.Text = s.ToString();
           
            progressBar1.Increment(12);
            label2.Text = progressBar1.Value.ToString();
            if (progressBar1.Value ==100)
            {
                timer1.Stop();
                //   MessageBox.Show("D0ne");
                this.Hide();
                Form3 f3 = new Form3();
                f3.Show();
            }
            
        }

        private void Form2_Load(object sender, EventArgs e)
        {
            timer1.Start();
        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void label1_Click(object sender, EventArgs e)
        {

        }
    }
}


```

