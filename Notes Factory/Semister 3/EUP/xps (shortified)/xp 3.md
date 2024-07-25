Definition of Classic Controls
Classic controls are components of the Windows operating system that allow users to interact with the system settings and configurations in a manner reminiscent of older Windows versions, such as Windows XP. These controls include various user interface elements such as buttons, text boxes, and menus that facilitate user actions like adjusting system settings, managing hardware, and configuring software.
Key Features:-
Control Panel: The Control Panel is a central component that houses various applets for managing system settings. It allows users to add or remove hardware and software, manage user accounts, and configure system preferences. In modern Windows versions, the Control Panel has been somewhat deprecated in favor of the Settings app, but it still exists and can be accessed for traditional settings management.
User Interaction: Classic controls are designed as child windows that enable user interaction within applications, often found in dialog boxes. They provide functionality for user input, command selection, and information display.
View Options: Users can switch between different views in the Control Panel, such as "Category" view and "Large/Small icons" view, which resemble the classic layout from earlier Windows versions. This flexibility allows users to navigate settings more comfortably according to their preferences.
Programming and Development: For developers, classic controls are implemented through the Windows API, specifically using libraries like User32.dll and Comctl32.dll. These controls require a moderate understanding of UI programming concepts.
Overall, classic controls in Windows serve as a bridge for users familiar with older versions of the operating system, providing a familiar interface for managing system settings and configurations.

Radio Button
A radio button is a graphical control element that allows users to select one option from a predefined set of mutually exclusive choices. When a user selects a radio button, any previously selected button in the same group is automatically deselected, ensuring that only one option can be active at a time. This is particularly useful in scenarios where a single choice is required, such as selecting a payment method or choosing a subscription plan. Radio buttons are visually represented as small circular buttons, typically accompanied by labels that describe the options they represent.
Text Box
A text box is an input control that allows users to enter and edit text. It is a versatile element used for various purposes, such as entering names, passwords, or search queries. Text boxes can be configured to accept single-line or multi-line input, depending on the requirements of the application. They are essential for collecting user input in forms and can have additional features like placeholder text and character limits.
Label
A label is a static control that displays text for informational purposes. Labels are typically used to describe other controls, such as text boxes or radio buttons, helping users understand what information is required or what options are available. Labels are non-interactive and cannot be edited by the user, serving purely as a guide within the user interface.
Button
A button is a fundamental user interface element that triggers an action when clicked by the user. Buttons are versatile and can be used for a variety of purposes, such as submitting forms, canceling actions, or executing commands. They are typically labeled with descriptive text to indicate their function, such as "OK", "Cancel", "Submit", or "Save".

Checkbox
A checkbox is a user interface element that allows users to make a binary choice, typically represented as a small square box that can be checked (selected) or unchecked (deselected). Checkboxes are often used when multiple options can be selected simultaneously, making them ideal for settings, preferences, and forms where users can choose one or more items from a list.

```csharp
        private void button1_Click(object sender, EventArgs e)
        {
            textBox1.Clear();
            textBox2.Clear();
            radioButton1.Checked = false;
            radioButton2.Checked = false;
            radioButton3.Checked = false;
            checkBox1.Checked = false; // Clear CheckBox 1
            checkBox2.Checked = false; // Clear CheckBox 2
            checkBox3.Checked = false; // Clear CheckBox 3
            checkBox4.Checked = false; // Clear CheckBox 4

        }

       private void button2_Click(object sender, EventArgs e)
       {
           string a = textBox1.Text;
           string b = textBox2.Text;
           if (a != " ")
           {
               MessageBox.Show("Name:- " + a);
           }
           else
           {
               MessageBox.Show("Write your name");
           }
           if (b != " ")
           {
               MessageBox.Show("SAP ID:- " + b);
           }

           else
           {
               MessageBox.Show("Write your SAP NO.");
           }

           string selectedOption = "";

           if (radioButton1.Checked)
           {
               selectedOption = radioButton1.Text; // Get text from RadioButton 1
           }
           else if (radioButton2.Checked)
           {
               selectedOption = radioButton2.Text; // Get text from RadioButton 2
           }
           else if (radioButton3.Checked)
           {
               selectedOption = radioButton3.Text; // Get text from RadioButton 3
           }
           if (!string.IsNullOrEmpty(selectedOption))
           {
               MessageBox.Show("You selected: " + selectedOption);
           }
           else
           {
               MessageBox.Show("Please select an option.");
           }

           string selectedOptions = "";

           if (checkBox1.Checked)
           {
               selectedOptions += checkBox1.Text + ", "; // Get text from CheckBox 1
           }
           if (checkBox2.Checked)
           {
               selectedOptions += checkBox2.Text + ", "; // Get text from CheckBox 2
           }
           if (checkBox3.Checked)
           {
               selectedOptions += checkBox3.Text + ", "; // Get text from CheckBox 3
           }
           if (checkBox4.Checked)
           {
               selectedOptions += checkBox4.Text + ", "; // Get text from CheckBox 4
           }
           if (!string.IsNullOrEmpty(selectedOptions))
           {
               MessageBox.Show("You selected: " + selectedOptions);
           }
           else
           {
               MessageBox.Show("Please select at least one option.");
           }

       }
       ```