# Lesson 5 — Photoresistor

## Objectives

* Understand what a photoresistor is and how it works.
* Learn the difference between **digital** and **analog** inputs.
* Use `analogRead()` to measure light.
* Learn how to store sensor readings using a variable.
* Use an `if` statement to create an automatic light.

---

## Part 1: What Is a Photoresistor?

[INSERT IMAGE OF PHOTORESISTOR HERE]

A **photoresistor**, also called a **Light Dependent Resistor (LDR)**, is a resistor whose resistance changes depending on the amount of light reaching it.

Generally:

* **More light** → Lower resistance
* **Less light** → Higher resistance

This allows us to use a photoresistor as a simple **light sensor**.

Photoresistors can be used for things such as:

* Automatic headlights
* Automatic night lights
* Light-sensitive alarms
* Robots that respond to their environment

---

## Part 2: Digital vs. Analog

Our push button from the previous lesson was a **digital input**.

It basically had two possible states:

**HIGH or LOW**

We can think about this as:

**YES or NO**

But light isn't always just "bright" or "dark."

A room could be:

**Very Dark → Dark → Medium → Bright → Very Bright**

Because there are many possible light levels, we can use an **analog input**.

---

## Pin Wiring Table

[INSERT TINKERCAD PHOTORESISTOR CIRCUIT IMAGE HERE]

In TinkerCAD, ensure that the provided circuit design template is connected like this:

| Component                    | Connect To                       |
| ---------------------------- | -------------------------------- |
| Photoresistor Circuit Output | **A0**                           |
| Voltage Divider              | **5V and GND**                   |
| LED Anode (+)                | **Pin 8 through 220 Ω resistor** |
| LED Cathode (-)              | **GND**                          |

The photoresistor is connected as part of a **voltage divider**, which allows the Arduino to measure changes in light as changes in voltage.

---

## Part 3: What Is `analogRead()`?

Previously, we used `digitalRead()` to read a button.

A digital input only gives us:

**HIGH or LOW**

For our photoresistor, we can use:

```cpp
analogRead(A0);
```

The Arduino Uno's `analogRead()` gives us a number between:

**0 and 1023**

Instead of only having two possible values, we now have over 1,000 possible measurements!

This allows the Arduino to detect different amounts of light.

---

## Part 4: What Is a Variable?

We want to save the measurement from our photoresistor.

We can do that using a **variable**.

A variable is like a **labeled box that stores information**.

For example:

```cpp
int lightLevel = analogRead(A0);
```

Here, we created a variable called:

`lightLevel`

The Arduino measures the voltage on A0 and stores the result inside `lightLevel`.

[INSERT TINKERCAD VARIABLE BLOCK IMAGE HERE]

If the amount of light changes, the value stored in `lightLevel` will also change the next time the Arduino reads the sensor.

---

## Part 5: Seeing the Sensor Value

We can use the **Serial Monitor** to see what our Arduino is measuring.

```cpp
Serial.println(lightLevel);
```

[INSERT SERIAL MONITOR IMAGE HERE]

Start the TinkerCAD simulation and change the amount of light reaching the photoresistor.

Watch what happens to the numbers!

Try observing the value when the photoresistor is:

* Very dark
* Medium
* Very bright

Depending on how the voltage divider is connected, the value may **increase or decrease** as the light becomes brighter.

---

## Part 6: Creating an Automatic Light

Now we can combine our photoresistor with the `if` statement from the push button lesson.

Suppose we decide that **500** is our dividing point between light and dark.

We could write:

```cpp
if (lightLevel < 500) {
    digitalWrite(8, HIGH);
}
else {
    digitalWrite(8, LOW);
}
```

This code is saying:

**IF** the light level is below 500 → Turn the LED ON.

**ELSE** → Turn the LED OFF.

Our complete system now looks like:

**Photoresistor → Arduino → Decision → LED**

The Arduino is responding automatically to its environment!

### What if my LED turns on at the wrong time?

Depending on how your photoresistor circuit is connected, your readings may work in the opposite direction.

If that happens, try changing:

```cpp
lightLevel < 500
```

to:

```cpp
lightLevel > 500
```

---

## Student Challenges

Try modifying the code to explore different behaviors:

* Find the sensor value when the environment is very dark.
* Find the sensor value when the environment is very bright.
* Choose your own threshold instead of `500`.
* Make an automatic night light.
* Reverse the behavior so the LED turns on when it is bright.
* Bonus: Add multiple LEDs that turn on at different light levels.

Don't stress about perfection — explore and observe!

---

## Quick Reference Table for Arduino Text Code

| Concept         | Function                      | Description                                |
| --------------- | ----------------------------- | ------------------------------------------ |
| Read sensor     | `analogRead(A0)`              | Reads an analog value from 0–1023          |
| Create variable | `int lightLevel`              | Creates a variable for our measurement     |
| Store reading   | `lightLevel = analogRead(A0)` | Saves the sensor measurement               |
| Print reading   | `Serial.println(lightLevel)`  | Displays the measurement                   |
| Compare         | `if (lightLevel < 500)`       | Checks the measurement against a threshold |
| LED ON          | `digitalWrite(8, HIGH)`       | Turns the LED on                           |
| LED OFF         | `digitalWrite(8, LOW)`        | Turns the LED off                          |

---
