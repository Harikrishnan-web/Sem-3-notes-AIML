**UNIT V – GUI PROGRAMMING (FULL THEORY NOTES – EXPANDED & COMPLETE)**
*(Short, clear, **covers EVERYTHING** from the PDF including all common methods, components, layout details, JavaFX architecture, lifecycle, etc.)*

---

# **1. SWING – INTRODUCTION**

* Part of **Java Foundation Classes (JFC)**.
* Extension of **AWT** with more powerful, flexible GUI tools.
* Components are **lightweight** (OS-independent).
* Fully written in Java → **portable**.
* Supports **MVC (Model–View–Controller)**.
* Used for **Standalone GUIs, Applets, Servlets UI**.
* Offers high-level components: **JTable, JList, JScrollPane, JColorChooser, JTabbedPane**, etc.
* Supports **Pluggable Look and Feel**.

---

# **2. FEATURES OF SWING**

* Set of APIs (classes + interfaces).
* Better event handling and drag-and-drop support.
* More flexible layouts.
* Pure Java implementation.
* “Lightweight components” (do not use native OS widgets).
* Swing components follow MVC internally.

---

# **3. SWING vs AWT**

| **AWT**          | **Swing**                      |
| ---------------- | ------------------------------ |
| Heavyweight      | Lightweight                    |
| OS-dependent     | Platform-independent           |
| Fewer components | Rich and powerful components   |
| No pluggable L&F | Supports pluggable Look & Feel |
| Uses `java.awt`  | Uses `javax.swing`             |

---

# **4. SWING COMPONENT HIERARCHY**

```
Object  
  ↳ Component  
      ↳ Container  
          ↳ JComponent  
              ↳ JFrame, JPanel, JButton, JTextField, JTable, etc.
```

---

# **5. COMMON SWING METHODS (VERY IMPORTANT)**

These appear repeatedly across almost all Swing components:

### **Component-level methods**

| Method                         | Use                             |
| ------------------------------ | ------------------------------- |
| **add(Component c)**           | Adds a component to a container |
| **setSize(int w, int h)**      | Sets width + height             |
| **setBounds(x, y, w, h)**      | Position + size                 |
| **setVisible(boolean b)**      | Shows/hides component           |
| **setLayout(LayoutManager m)** | Sets layout manager             |
| **setBackground(Color c)**     | Sets background color           |
| **setForeground(Color c)**     | Sets text/foreground color      |
| **setEnabled(boolean)**        | Enables/disables component      |
| **setFont(Font f)**            | Changes font                    |
| **getText() / setText()**      | Used in text-based components   |

### **JFrame specific**

| Method                               | Use                          |
| ------------------------------------ | ---------------------------- |
| **setTitle(String t)**               | Sets window title            |
| **setDefaultCloseOperation(int op)** | Behavior when closing window |
| **setResizable(boolean)**            | Resize enable/disable        |

---

# **6. MODEL–VIEW–CONTROLLER (MVC)**

### **Model**

* Holds application data.
* Contains getters & setters.
* May notify controller when data changes.

### **View**

* Displays model data.
* Does not store logic.
* Only presentation.

### **Controller**

* Handles user actions.
* Updates the model.
* Refreshes the view.

### **MVC Request Flow**

1. User → Controller
2. Controller → Model (read/update)
3. Model → Controller (data ready)
4. Controller → View (display)

### **Advantages**

* Clean separation of concerns
* Easy to maintain, modify, test
* Code reusability (one model → many views)
* Parallel development possible

---

# **7. LAYOUT MANAGEMENT IN JAVA**

Layout managers organize components inside containers.

---

## **BorderLayout**

* Divides area into **5 regions**:
  **NORTH, SOUTH, EAST, WEST, CENTER**
* Only **one component per region**.

### **Constants**

* `BorderLayout.NORTH`
* `BorderLayout.SOUTH`
* `BorderLayout.EAST`
* `BorderLayout.WEST`
* `BorderLayout.CENTER`

### **Constructors**

* `BorderLayout()` – no gaps
* `BorderLayout(int hgap, int vgap)` – with spacing

### **Important rule**

If region is NOT given → **last added component fills entire frame**.

---

# **8. INTRODUCTION TO JAVAFX**

JavaFX = modern successor to Swing.

### **Key Points**

* Used to build **Desktop, Web-embedded, Mobile UI**.
* Hardware-accelerated graphics.
* Uses **FXML** (XML-style UI definition).
* Supports **CSS-like styling**.
* Drag-and-drop **Scene Builder** tool.
* Interoperable with Swing via **SwingNode**.
* Offers rich UI controls.
* Supports 2D, 3D, animation, audio/video.

---

# **9. FEATURES OF JAVAFX**

| Feature                      | Explanation                      |
| ---------------------------- | -------------------------------- |
| **Java Library**             | Rich GUI classes                 |
| **FXML**                     | Declarative UI language          |
| **Scene Builder**            | Drag & drop UI designer          |
| **WebView**                  | Embeds web pages (WebKit engine) |
| **Built-in Controls**        | Buttons, tables, menus, lists…   |
| **CSS Styling**              | GUI styled like a webpage        |
| **Swing Interop**            | Use Swing + JavaFX together      |
| **Canvas API**               | Freehand 2D drawing              |
| **3D Support**               | Shapes, lights, camera           |
| **Media Engine**             | Audio/video playback             |
| **Self-contained Packaging** | Bundles Java + FX runtime        |

---

# **10. JAVA FX ARCHITECTURE**

### **1. JavaFX API**

Main packages:

* `javafx.animation` – transitions, fades, moves
* `javafx.css` – styling elements
* `javafx.geometry` – shapes, 2D
* `javafx.scene` – **Scene Graph** + subpackages
* `javafx.application` – app lifecycle
* `javafx.event` – event handling
* `javafx.stage` – top-level windows

---

### **2. Scene Graph**

Everything in JavaFX is a **Node**.

Nodes are:

* **Root node** – no parent
* **Branch node** – parent + children
* **Leaf node** – has no children

Scene Graph = tree of UI elements.

---

### **3. Quantum Toolkit**

* Connects top-level API with low-level engines.
* Bridges Prism + Glass.

---

### **4. Prism**

* Graphics rendering pipeline.
* Hardware accelerated → fast, smooth UI.

---

### **5. Glass Windowing Toolkit**

* Communicates with OS.
* Handles events, windows, timers, surfaces.

---

### **6. WebView**

* Embeds web pages using **WebKit HTML engine**.

---

### **7. Media Engine**

* Audio/video playback using **GStreamer**.
* Low-latency media pipeline.

---

# **11. JAVAFX APPLICATION LIFE CYCLE**

### **Methods**

| Method                        | Description                             |
| ----------------------------- | --------------------------------------- |
| **init()**                    | Called first, cannot create stage/scene |
| **start(Stage primaryStage)** | Main UI code                            |
| **stop()**                    | Cleanup when closing                    |

### **launch()**

* Static method that starts JavaFX application.
* Must be called from `main()`.

### **Order of Execution**

1. JavaFX runtime creates application object
2. **init()**
3. **start()**
4. Application runs
5. **stop()**

---

# **12. TERMINATING JAVAFX APPS**

### **Automatic termination**

* When last window closes → app stops.

### **Prevent auto-exit**

`Platform.setImplicitExit(false);`

### **Manual exit**

* `Platform.exit()`
* `System.exit(int)`

---

# **13. SUMMARY OF ALL IMPORTANT TERMS**

* Swing = JFC extension, lightweight, supports MVC.
* AWT = heavyweight, OS-dependent.
* MVC = Model (data), View (UI), Controller (logic).
* BorderLayout = 5-region layout manager.
* JavaFX = modern GUI toolkit replacing Swing.
* JavaFX API contains animation, CSS, scene graph, media, web engine.
* JavaFX lifecycle = init → start → stop.

---
# **SWING PROGRAMS**

---

# **1. First Swing Example**

## **Code**

```java
import javax.swing.*;

public class FirstSwing {
    public static void main(String[] args) {
        JFrame f = new JFrame("First Swing");
        JButton b = new JButton("Click");
        b.setBounds(130, 100, 100, 40);
        f.add(b);
        f.setSize(400, 500);
        f.setLayout(null);
        f.setVisible(true);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
}
```

## **Output**

A window opens with the title **“First Swing”**.
The background is plain, and at coordinates (130,100) a button appears.
The button displays the text **“Click”** in the center.
Nothing happens on clicking the button because no event is attached.
The window size is 400×500 pixels and remains open until closed manually.

---

# **2. Swing Using Constructor**

## **Code**

```java
import javax.swing.*;

public class SimpleSwing {
    SimpleSwing() {
        JFrame f = new JFrame("Simple");
        JButton b = new JButton("Click");
        b.setBounds(130, 100, 100, 40);
        f.add(b);
        f.setSize(400, 500);
        f.setLayout(null);
        f.setVisible(true);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new SimpleSwing();
    }
}
```

## **Output**

A window titled **“Simple”** appears.
The same button labeled **“Click”** is displayed at the same position.
The layout is manually controlled, and the button stays fixed.
No event is attached, so clicking it has no effect.
The window stays visible until closed.

---

# **3. BorderLayout – Basic**

## **Code**

```java
import javax.swing.*;
import java.awt.*;

public class BorderLayoutDemo {
    BorderLayoutDemo() {
        JFrame f = new JFrame("BorderLayout");
        f.add(new JButton("NORTH"), BorderLayout.NORTH);
        f.add(new JButton("SOUTH"), BorderLayout.SOUTH);
        f.add(new JButton("EAST"), BorderLayout.EAST);
        f.add(new JButton("WEST"), BorderLayout.WEST);
        f.add(new JButton("CENTER"), BorderLayout.CENTER);
        f.setSize(300,300);
        f.setVisible(true);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new BorderLayoutDemo();
    }
}
```

## **Output**

A 300×300 window opens titled **“BorderLayout”**.
Five buttons appear automatically sized according to BorderLayout regions:

* **NORTH** button spans the top width,
* **SOUTH** button spans the bottom width,
* **EAST** button sticks vertically on the right,
* **WEST** button sticks vertically on the left,
* **CENTER** button fills the remaining space.
  All buttons are visible and arranged cleanly without overlap.

---

# **4. BorderLayout with Gaps**

## **Code**

```java
import javax.swing.*;
import java.awt.*;

public class BorderLayoutGap {
    BorderLayoutGap() {
        JFrame f = new JFrame("Border Gap Layout");
        f.setLayout(new BorderLayout(20,15));
        f.add(new JButton("NORTH"), BorderLayout.NORTH);
        f.add(new JButton("SOUTH"), BorderLayout.SOUTH);
        f.add(new JButton("EAST"), BorderLayout.EAST);
        f.add(new JButton("WEST"), BorderLayout.WEST);
        f.add(new JButton("CENTER"), BorderLayout.CENTER);
        f.setSize(300,300);
        f.setVisible(true);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new BorderLayoutGap();
    }
}
```

## **Output**

A window identical to the basic BorderLayout example appears,
but there are **visible spaces** between the regions.
A horizontal gap of 20 pixels and vertical gap of 15 pixels clearly separates the buttons.
The CENTER button has space around it, making the layout visually more open and spaced-out.

---

# **5. BorderLayout Without Region**

## **Code**

```java
import javax.swing.*;
import java.awt.*;

public class BorderNoRegion {
    BorderNoRegion() {
        JFrame f = new JFrame("No Region");
        f.setLayout(new BorderLayout());
        f.add(new JButton("ONE"));
        f.add(new JButton("TWO"));
        f.add(new JButton("THREE"));
        f.add(new JButton("FOUR"));
        f.add(new JButton("Visible Button"));
        f.setSize(300,300);
        f.setVisible(true);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new BorderNoRegion();
    }
}
```

## **Output**

A 300×300 window opens.
Although five buttons are added, only the **last added** one appears.
The visible button covers the **entire window area**.
This happens because adding components without specifying regions replaces previous ones in BorderLayout.

---

# **MVC PROGRAMS**

---

# **6. MVC – Model**

## **Code**

```java
public class Employee {
    private String name, id, department;

    public String getName() { return name; }
    public void setName(String n) { name = n; }

    public String getId() { return id; }
    public void setId(String i) { id = i; }

    public String getDepartment() { return department; }
    public void setDepartment(String d) { department = d; }
}
```

## **Output**

No output.
This class purely stores data using getters and setters.

---

# **7. MVC – View**

## **Code**

```java
public class EmployeeView {
    public void printEmployeeDetails(String name, String id, String dept) {
        System.out.println("Employee Details:");
        System.out.println("Name: " + name);
        System.out.println("Employee ID: " + id);
        System.out.println("Employee Department: " + dept);
    }
}
```

## **Output**

When called, it prints employee details neatly in console.
Each attribute appears on a new line in a readable format.

---

# **8. MVC – Controller**

## **Code**

```java
public class EmployeeController {
    private Employee model;
    private EmployeeView view;

    public EmployeeController(Employee m, EmployeeView v) {
        model = m;
        view = v;
    }

    public void setEmployeeName(String n) { model.setName(n); }
    public String getEmployeeName() { return model.getName(); }

    public void setEmployeeId(String id) { model.setId(id); }
    public String getEmployeeId() { return model.getId(); }

    public void setEmployeeDepartment(String d) { model.setDepartment(d); }
    public String getEmployeeDepartment() { return model.getDepartment(); }

    public void updateView() {
        view.printEmployeeDetails(model.getName(), model.getId(), model.getDepartment());
    }
}
```

## **Output**

The controller itself has no visual output.
It updates model values and asks the view to print the updated details.
Output appears only when updateView() is executed.

---

# **9. MVC – Main**

## **Code**

```java
public class MVCMain {
    public static void main(String[] args) {
        Employee model = new Employee();
        model.setName("Anu");
        model.setId("11");
        model.setDepartment("Salesforce");

        EmployeeView view = new EmployeeView();
        EmployeeController controller = new EmployeeController(model, view);

        controller.updateView();

        controller.setEmployeeName("Nirnay");
        System.out.println("\nEmployee Details after updating:");
        controller.updateView();
    }
}
```

## **Output**

A clear two-part output in the console:

```
Employee Details:
Name: Anu
Employee ID: 11
Employee Department: Salesforce

Employee Details after updating:
Name: Nirnay
Employee ID: 11
Employee Department: Salesforce
```

The first section shows initial model values.
The second section shows updated name while ID and department remain same.

---

# **JAVAFX PROGRAMS**

---

# **10. JavaFX Basic Window**

## **Code**

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class FXBasic extends Application {
    public void start(Stage s) {
        s.setTitle("Hello JavaFX");
        s.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
```

## **Output**

A JavaFX window opens with the title **“Hello JavaFX”**.
The window is empty (no controls inside).
It is blank except for the default background.
The window remains open until manually closed.

---

# **11. JavaFX Button Interaction**

## **Code**

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class FXButton extends Application {
    public void start(Stage s) {
        Button b = new Button("Click Me");
        b.setOnAction(e -> b.setText("Clicked"));
        StackPane root = new StackPane(b);
        s.setScene(new Scene(root,300,200));
        s.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
```

## **Output**

A 300×200 window appears.
A button labeled **“Click Me”** sits centered in the screen.
When clicked once, the text changes to **“Clicked”**.
The change stays permanently for the window session.

---

# **12. JavaFX Mini Calculator**

## **Code**

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class FXCalculator extends Application {
    public void start(Stage s) {
        TextField t1 = new TextField();
        TextField t2 = new TextField();
        Button add = new Button("Add");
        Label result = new Label();

        add.setOnAction(e -> {
            int a = Integer.parseInt(t1.getText());
            int b = Integer.parseInt(t2.getText());
            result.setText("Sum: " + (a + b));
        });

        VBox v = new VBox(10, t1, t2, add, result);
        s.setScene(new Scene(v,300,200));
        s.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
```

## **Output**

A simple calculator window opens.
Two empty text fields appear stacked vertically.
Below them sits an **Add** button.
Below the button, an empty label is shown.
When numbers such as **5** and **8** are entered and Add is clicked,
the label updates to:

```
Sum: 13
```

The result updates each time new values are entered and Add is pressed.

---

