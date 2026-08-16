Here are three separate Java programs using AWT (Abstract Window Toolkit) components to handle mouse events, key events, and window closing events. 

### 1. Handling Mouse Events

This program will demonstrate how to handle various mouse events using AWT components.

```java
import java.awt.*;
import java.awt.event.*;

public class MouseEventExample extends Frame implements MouseListener {
    
    Label label;

    public MouseEventExample() {
        label = new Label("Mouse Events will be displayed here");
        label.setBounds(20, 50, 300, 30);
        
        add(label);
        setSize(400, 200);
        setLayout(null);
        setVisible(true);

        addMouseListener(this);
        
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });
    }

    public void mouseClicked(MouseEvent e) {
        label.setText("Mouse Clicked at (" + e.getX() + ", " + e.getY() + ")");
    }

    public void mouseEntered(MouseEvent e) {
        label.setText("Mouse Entered");
    }

    public void mouseExited(MouseEvent e) {
        label.setText("Mouse Exited");
    }

    public void mousePressed(MouseEvent e) {
        label.setText("Mouse Pressed");
    }

    public void mouseReleased(MouseEvent e) {
        label.setText("Mouse Released");
    }

    public static void main(String[] args) {
        new MouseEventExample();
    }
}
```

### 2. Implementing Key Listener to Handle Key Events

This program will demonstrate how to handle key events using the KeyListener interface.

```java
import java.awt.*;
import java.awt.event.*;

public class KeyEventExample extends Frame implements KeyListener {
    
    TextArea textArea;

    public KeyEventExample() {
        textArea = new TextArea();
        textArea.setBounds(20, 50, 300, 100);
        
        add(textArea);
        setSize(400, 200);
        setLayout(null);
        setVisible(true);

        textArea.addKeyListener(this);
        
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.exit(0);
            }
        });
    }

    public void keyPressed(KeyEvent e) {
        textArea.append("Key Pressed: " + e.getKeyChar() + "\n");
    }

    public void keyReleased(KeyEvent e) {
        textArea.append("Key Released: " + e.getKeyChar() + "\n");
    }

    public void keyTyped(KeyEvent e) {
        textArea.append("Key Typed: " + e.getKeyChar() + "\n");
    }

    public static void main(String[] args) {
        new KeyEventExample();
    }
}
```

### 3. Handling Window Closing Event

This program demonstrates how to handle the window closing event using AWT components.

```java
import java.awt.*;
import java.awt.event.*;

public class WindowCloseExample extends Frame {
    
    public WindowCloseExample() {
        setSize(400, 200);
        setLayout(new FlowLayout());
        setTitle("Window Closing Event Example");
        setVisible(true);
        
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent we) {
                System.out.println("Window Closing Event Triggered");
                System.exit(0);
            }
        });
    }

    public static void main(String[] args) {
        new WindowCloseExample();
    }
}
```

### Instructions to Run the Programs
1. Make sure you have Java Development Kit (JDK) installed.
2. Copy each code block into a separate file with the same name as the class (e.g., `MouseEventExample.java`, `KeyEventExample.java`, `WindowCloseExample.java`).
3. Compile each program using the command: `javac FileName.java`.
4. Run each program using the command: `java FileName`.

These programs provide a basic understanding of handling different types of events using AWT components in Java.