# Lesson 7 — Final Challenge

## Objectives

* Combine multiple components from previous lessons into one complete system.
* Practice designing a circuit without being given every step.
* Use sensors, decisions, and outputs together.
* Apply programming concepts such as variables, `if` statements, and delays.
* Learn how to use a more advanced TinkerCAD component.

---

# Part 1 — Challenge 1: Smart Parking Gate

For your first final challenge, you will build a **Smart Parking Gate**.

The system should detect when an object approaches, open a gate using a servo motor, and use LEDs to show whether the gate is open or closed.

This challenge combines several concepts from previous lessons.

You will use:

* **Ultrasonic Sensor** — Detect an approaching object
* **Servo Motor** — Open and close the gate
* **Red LED** — Show that the gate is closed
* **Green LED** — Show that the gate is open
* **Arduino** — Read the sensor and control the outputs

---

## How Should the System Work?

Your parking gate should follow these rules:

### No Object Nearby

If the ultrasonic sensor detects that the object is far away:

* Servo should stay at **0°**
* Red LED should be **ON**
* Green LED should be **OFF**

This represents a closed gate.

### Object Approaches

If an object comes within a certain distance, such as **15 cm**:

* Servo should rotate to approximately **90°**
* Red LED should turn **OFF**
* Green LED should turn **ON**

This represents an open gate.

### Object Leaves

Once the object moves away again:

* Servo should return to **0°**
* Red LED should turn back **ON**
* Green LED should turn **OFF**

---

## Input → Process → Output

Think about the system using the pattern from the introduction.

**INPUT → PROCESS → OUTPUT**

For this project:

**Ultrasonic Sensor → Arduino → Servo + LEDs**

The ultrasonic sensor measures distance.

The Arduino checks that distance.

The Arduino then decides whether the gate should be open or closed.

---

## Suggested Components

Add the following components to your TinkerCAD circuit:

| Component                 | Amount |
| ------------------------- | ------ |
| Arduino Uno               | 1      |
| Breadboard                | 1      |
| HC-SR04 Ultrasonic Sensor | 1      |
| Servo Motor               | 1      |
| Red LED                   | 1      |
| Green LED                 | 1      |
| 220 Ω Resistors           | 2      |

You may choose your own Arduino pins, but make sure your code matches your wiring!

---

## Suggested Behavior

A useful starting point might be:

```cpp
if (distance < 15) {

    // Open gate

}
else {

    // Close gate

}
```

Inside the `if` statement, think about what should happen to:

* The servo
* The red LED
* The green LED

Then think about what should happen inside the `else`.

---

## Questions to Think About

Before building your circuit, answer these questions:

* What component is the **input**?
* What components are the **outputs**?
* What distance should cause the gate to open?
* What angle represents an open gate?
* What angle represents a closed gate?
* Which LED should be on when the gate is closed?
* Which LED should be on when the gate is open?

---

## Minimum Requirements

Your Smart Parking Gate must:

* Measure distance using the ultrasonic sensor.
* Store the distance measurement in a variable.
* Use an `if` statement.
* Open the servo when an object is nearby.
* Close the servo when the object moves away.
* Use a red LED for **closed**.
* Use a green LED for **open**.

---

## Bonus Challenges

Once your basic system works, try improving it!

### Bonus 1 — Add a Delay

When an object approaches:

1. Open the gate.
2. Keep it open for several seconds.
3. Close it again.

---

### Bonus 2 — Print the Distance

Use the Serial Monitor to display:

```cpp
Distance: 14 cm
```

You could also print:

```cpp
Gate Open
```

or:

```cpp
Gate Closed
```

---

### Bonus 3 — Add a Warning Zone

Create three possible states.

For example:

* More than 30 cm → Green
* Between 15 and 30 cm → Yellow
* Less than 15 cm → Gate opens

This may require another LED and additional `if` statements.

---

### Bonus 4 — Add a Button

Add a button that manually opens the gate.

Now your system has **two different inputs**:

**Ultrasonic Sensor + Button → Arduino → Servo**

Think about how either input could cause the gate to open.

---

# Part 2 — Challenge 2: Learn a New Component

For the second challenge, you will learn how to use a component that we have not used before:

# 16x2 LCD Display

[INSERT IMAGE OF 16x2 LCD HERE]

An **LCD**, or **Liquid Crystal Display**, allows the Arduino to display words and numbers.

A **16x2 LCD** can display:

* 16 characters across
* 2 rows of text

For example:

```text
Distance:
14.3 cm
```

Instead of only seeing information in the Serial Monitor, we can now display information directly on our circuit!

---

## Why Is This More Difficult?

The components from earlier lessons usually required only a few wires.

An LCD requires:

* More connections
* Multiple Arduino pins
* A library
* Initialization code
* Commands for placing and displaying text

This makes it a great final component to learn.

Don't worry if it looks complicated at first.

The goal is to understand the general idea and get something working.

---

## What Is a Library?

To control the LCD, Arduino uses something called a **library**.

A library is a collection of pre-written code that makes complicated components easier to use.

Instead of writing all the low-level LCD control code ourselves, we can use the built-in:

```cpp
LiquidCrystal
```

library.

At the top of your program, you will see:

```cpp
#include <LiquidCrystal.h>
```

This tells Arduino:

> I want to use the LiquidCrystal library.

---

## LCD Pin Wiring

A standard 16x2 LCD has many pins.

Your TinkerCAD design may use wiring similar to this:

| LCD Pin | Connect To               |
| ------- | ------------------------ |
| VSS     | **GND**                  |
| VDD     | **5V**                   |
| VO      | **Potentiometer output** |
| RS      | **Arduino Pin 12**       |
| RW      | **GND**                  |
| E       | **Arduino Pin 11**       |
| D4      | **Arduino Pin 5**        |
| D5      | **Arduino Pin 4**        |
| D6      | **Arduino Pin 3**        |
| D7      | **Arduino Pin 2**        |
| A       | **5V through resistor**  |
| K       | **GND**                  |

[INSERT LCD TINKERCAD CIRCUIT IMAGE HERE]

The LCD uses several wires because the Arduino needs to send both **commands** and **data** to the display.

---

## What Is the Potentiometer Doing?

You may notice a **potentiometer** connected to the LCD.

[INSERT POTENTIOMETER IMAGE HERE]

A potentiometer is an adjustable resistor.

For the LCD, it controls the **screen contrast**.

If the screen appears blank, the code may actually be working!

Try turning the potentiometer.

Too much or too little contrast can make the characters difficult to see.

---

## Basic LCD Code

First, include the LCD library:

```cpp
#include <LiquidCrystal.h>
```

Then tell Arduino which pins are connected to the LCD:

```cpp
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
```

Inside `setup()`:

```cpp
lcd.begin(16, 2);
```

This tells the Arduino that we are using an LCD with:

* 16 columns
* 2 rows

---

## Displaying Text

To display text:

```cpp
lcd.print("Hello!");
```

The LCD will display:

```text
Hello!
```

---

## Moving to the Second Row

We can use:

```cpp
lcd.setCursor(0, 1);
```

The first number represents the column.

The second number represents the row.

Remember that counting starts at **0**.

So:

```cpp
lcd.setCursor(0, 0);
```

means:

**First column, first row**

and:

```cpp
lcd.setCursor(0, 1);
```

means:

**First column, second row**

---

## Basic Example

Try displaying two lines:

```cpp
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {

    lcd.begin(16, 2);

    lcd.print("ECE Workshop!");

    lcd.setCursor(0, 1);

    lcd.print("Hello!");

}

void loop() {

}
```

Your LCD should display something similar to:

```text
ECE Workshop!
Hello!
```

---

# LCD Challenge

Once you can display basic text, your goal is to connect the LCD to something you learned earlier.

You can choose one of the following challenges.

---

## Option 1 — Distance Display

Connect an ultrasonic sensor and display its measurement.

Your LCD might show:

```text
Distance:
18.4 cm
```

The system becomes:

**Ultrasonic Sensor → Arduino → LCD**

---

## Option 2 — Light Level Display

Connect your photoresistor.

Display the light measurement:

```text
Light Level:
725
```

You could also display a message:

```text
Light:
BRIGHT
```

or:

```text
Light:
DARK
```

---

## Option 3 — Button Counter

Connect a push button.

Each time the button is pressed, increase a number.

The LCD could show:

```text
Button Presses:
7
```

This option is more difficult because you must keep track of how many times the button has been pressed.

---

# Final Mega Challenge

If you finish both parts early, combine everything!

Take your **Smart Parking Gate** from Challenge 1 and add the LCD.

The LCD could display:

```text
Distance: 12 cm
Gate Open
```

or:

```text
Distance: 40 cm
Gate Closed
```

Now your system contains:

**INPUT**

Ultrasonic Sensor

↓

**PROCESS**

Arduino

↓

**OUTPUTS**

Servo + LEDs + LCD

This is the same **Input → Process → Output** idea from the beginning of the workshop, just with a much more advanced circuit!

---

# Student Design Challenge

If you want an even bigger challenge, create your **own circuit**.

Your circuit must contain:

* At least **one input**
* At least **two outputs**
* At least one `if` statement

Possible inputs include:

* Push button
* Photoresistor
* Ultrasonic sensor

Possible outputs include:

* LED
* Servo motor
* DC motor
* LCD

Before building, write down:

**Input:** ____________________

**Outputs:** ____________________

**What should happen?**

---

---

Then build and test your idea in TinkerCAD!

---

# Quick Reference Table for LCD Text Code

| Concept         | Function                     | Description                                   |
| --------------- | ---------------------------- | --------------------------------------------- |
| Include library | `#include <LiquidCrystal.h>` | Loads the LCD library                         |
| Create LCD      | `LiquidCrystal lcd(...)`     | Defines the Arduino pins connected to the LCD |
| Start LCD       | `lcd.begin(16, 2)`           | Configures a 16x2 display                     |
| Display text    | `lcd.print()`                | Displays text or numbers                      |
| Move cursor     | `lcd.setCursor()`            | Changes where text appears                    |
| Clear screen    | `lcd.clear()`                | Removes everything from the LCD               |

---

# 🎉 Workshop Complete!

You've now worked with:

* LEDs
* Push buttons
* Servo motors
* DC motors
* Photoresistors
* Ultrasonic sensors
* LCD displays

More importantly, you've learned how electronic systems are built using:

**INPUT → PROCESS → OUTPUT**

You've also practiced:

* Wiring circuits
* Using Arduino pins
* Reading sensors
* Controlling outputs
* Variables
* `if` statements
* `for` loops
* `delay()`
* Analog and digital signals
* Serial Monitor
* Arduino libraries

You do not need to memorize every command or every circuit.

Engineering is about understanding the ideas, experimenting, testing, and figuring out why something does or doesn't work.

If you can look at a new component and start asking:

**What does it need for power?**

**What signal does it send or receive?**

**What Arduino pin should it connect to?**

**How can I use it as an input or output?**

then you're already thinking like an engineer.

---
