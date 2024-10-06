```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Data.SqlClient;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
namespace WindowsFormsApp23
{
    public partial class Form1 : Form
    {
        SqlConnection conn;
        public Form1()
        {
            InitializeComponent();
            conn = new SqlConnection(@"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=C:\Users\SBMPC.Student\source\repos\WindowsFormsApp23\Database1.mdf;Integrated Security=True");
        }
        private void button1_Click(object sender, EventArgs e)
        {
            string query = "Insert into [customer_details] (name , id , contact , age) Values(@name , @id , @contact , @age);";
            SqlCommand cmd = new SqlCommand(query, conn);
            cmd.Parameters.AddWithValue("@name", textBox1.Text);
            cmd.Parameters.AddWithValue("@id", textBox2.Text);
            cmd.Parameters.AddWithValue("@contact", textBox3.Text);
            cmd.Parameters.AddWithValue("@age", textBox4.Text);
            conn.Open();
            SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
            DataTable dt = new DataTable();
            adapter.Fill(dt);
              MessageBox.Show("Saved");
    conn.Close();}
        private void button2_Click(object sender, EventArgs e)
        {  if (dataGridView1.SelectedRows.Count > 0)
            {
                DataGridViewRow selected = dataGridView1.SelectedRows[0];
                string name = selected.Cells[0].Value.ToString();                string query = "Delete from [customer_details] where name = @name ;";
                SqlCommand cmd = new SqlCommand(query, conn);
                cmd.Parameters.AddWithValue("@name", name);
                conn.Open();
                SqlDataAdapter adapter = new SqlDataAdapter(cmd);
                DataTable dt = new DataTable();
                adapter.Fill(dt);
                MessageBox.Show("Deleted");
                conn.Close();
            }
        }
        private void button3_Click(object sender, EventArgs e)
        {
            string query = "select * from [customer_details];";
            conn.Open();
            SqlDataAdapter adapter = new SqlDataAdapter(query,conn);
            DataTable dt = new DataTable();
            adapter.Fill(dt);   
            dataGridView1.DataSource= dt;
            conn.Close();
        }
        private void button4_Click_1(object sender, EventArgs e)
        {
            if (dataGridView1.SelectedRows.Count > 0)
            {
                DataGridViewRow selected = dataGridView1.SelectedRows[0];
                string id = selected.Cells["id"].Value.ToString();
                string query = "UPDATE [customer_details] SET name = @name, contact = @contact, age = @age WHERE id = @id;";
                SqlCommand cmd = new SqlCommand(query, conn);
                cmd.Parameters.AddWithValue("@name", textBox1.Text);
                cmd.Parameters.AddWithValue("@contact", textBox3.Text);
                cmd.Parameters.AddWithValue("@age", textBox4.Text);
                cmd.Parameters.AddWithValue("@id", id); 
                    conn.Open();
                    cmd.ExecuteNonQuery(); 
                    MessageBox.Show("Updated");
                    string selectQuery = "SELECT * FROM [customer_details];";
                  SqlDataAdapter adapter = new SqlDataAdapter(selectQuery, conn);
                    DataTable dt = new DataTable();
                    adapter.Fill(dt);
                    dataGridView1.DataSource = dt;
                    conn.Close();
            }
        }
            
    }
}