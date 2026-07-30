# Lesson 3 — Push Button

## Objectives

* Understand what a push button is and how it works.
* Learn the difference between an **input** and an **output**.
* Learn how Arduino detects whether a button is pressed.
* Use an `if` statement to make decisions.
* Control an LED using a push button.

---

## Part 1: What Is a Push Button?

<img width="164" height="158" alt="image" src="https://github.com/user-attachments/assets/f3c844e4-85a4-4655-b766-5d78a6d5e2ce" />

A **push button** is a simple type of switch.

When you press the button, you change an electrical connection. The Arduino can detect this change and respond to it.

This introduces one of the most important ideas in robotics:

**INPUT → PROCESS → OUTPUT**

For our circuit:

**Push Button → Arduino → LED**

The push button gives the Arduino an **input**.

The Arduino processes that information.

The LED is the **output** that the Arduino controls.

---

## Pin Wiring Table

In TinkerCAD, ensure that the circuit design template is connected like this:

| Component         | Connect To                       |
| ----------------- | -------------------------------- |
| LED Anode (+)     | **Pin 8 through 220 Ω resistor** |
| LED Cathode (-)   | **GND**                          |
| Button Signal     | **Pin 2**                        |
| Button Other Side | **GND**                          |



For this activity, we will use Arduino's built-in **INPUT_PULLUP** resistor for the button.

---

## Part 2: What Is `digitalRead()`?

Previously, we used:

```cpp
digitalWrite(8, HIGH);
```

to **send** a signal from the Arduino.

Now we want to receive an input.

For that, we can use:

```cpp
digitalRead(2);
```

`digitalRead()` asks the Arduino to check whether a pin is currently **HIGH** or **LOW**.

In our example, we are checking **pin 2**, where our button is connected.

---

## Part 3: What Is an `if` Statement?

An `if` statement allows our Arduino to **make a decision**.

You can think about an `if` statement like this:

**IF** it is raining, **THEN** bring an umbrella.

Our Arduino can make a similar decision:

**IF** the button is pressed, **THEN** turn on the LED.

The Arduino text code would look like this:

```cpp
if (digitalRead(2) == LOW) {
    digitalWrite(8, HIGH);
}
```

<img width="360" height="250" alt="image" src="https://github.com/user-attachments/assets/c5c3c1d5-0c3a-4e2f-947d-e0d5bdb0510b" />

---

## Why Does Pressed Equal `LOW`?

Because we are using `INPUT_PULLUP`, the Arduino normally holds the button input at **HIGH**.

When the button is pressed, pin 2 becomes connected to **GND**.

That makes the input **LOW**.

| Button State | Arduino Reads |
| ------------ | ------------- |
| Not Pressed  | **HIGH**      |
| Pressed      | **LOW**       |

It may seem backwards at first, but this is a very common way to connect buttons to an Arduino!

---

## Part 4: What Is `else`?

What if we also want something to happen when the button is **not** pressed?

We can use an `else` statement.

```cpp
if (digitalRead(2) == LOW) {
    digitalWrite(8, HIGH);
}
else {
    digitalWrite(8, LOW);
}
```

This code is saying:

**IF** the button is pressed → Turn the LED ON.

**ELSE** → Turn the LED OFF.

This allows our Arduino to choose between two different actions.

---

## Student Challenges

Try modifying the code to explore different behaviors:

* Make the LED turn **OFF when the button is pressed** and ON when it is released.
* Make the LED blink while the button is being held.
* Add a second LED and make the LEDs alternate depending on the button.
* Bonus: Try making something happen only after the button has been pressed.

Don't stress about perfection — explore and observe!

---

## Quick Reference Table for Arduino Text Code

| Concept        | Function                   | Description                         |
| -------------- | -------------------------- | ----------------------------------- |
| Button input   | `pinMode(2, INPUT_PULLUP)` | Sets pin 2 as a button input        |
| Read button    | `digitalRead(2)`           | Reads HIGH or LOW from the button   |
| If statement   | `if (...)`                 | Runs code if a condition is true    |
| Else statement | `else`                     | Runs code if the condition is false |
| LED ON         | `digitalWrite(8, HIGH)`    | Turns the LED on                    |
| LED OFF        | `digitalWrite(8, LOW)`     | Turns the LED off                   |

---
