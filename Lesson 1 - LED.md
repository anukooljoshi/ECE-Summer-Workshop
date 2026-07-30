# Lesson 2 — LED Basics

## Objectives

* Understand what an LED is and how it works.
* Learn how to control an LED in TinkerCAD.
* Understand the difference between **HIGH** and **LOW**.
* Use `delay()` to make an LED blink.
* Experiment with different blinking patterns.

---

## Part 1: What Is an LED?

<img width="1388" height="1020" alt="image" src="https://github.com/user-attachments/assets/46be8159-2b26-4e88-aaab-52852298db61" />

An **LED**, or **Light Emitting Diode**, is a small electronic component that produces light when electricity flows through it.

LEDs are used everywhere in electronics. For example, they can be used as:

* Power indicators
* Warning lights
* Robot headlights
* Status indicators

An LED has two legs:

* **Anode (+)** — the longer leg
* **Cathode (-)** — the shorter leg

The anode connects toward the positive side of the circuit, while the cathode connects toward **GND**.

Another way to think about it: an LED is like a **tiny controllable light bulb** that our Arduino can turn on and off.

---

## Why Do We Need a Resistor?

<img width="414" height="162" alt="image" src="https://github.com/user-attachments/assets/8bfc5b45-7dfd-48b0-9f9a-6af989407328" />

We should not connect an LED directly between an Arduino output pin and GND.

The Arduino can provide more current than the LED needs. A **resistor** limits the amount of current flowing through the LED and protects it.

For this activity, we will use a **220 Ω resistor**.

---

## Pin Wiring Table

In TinkerCAD, ensure that the circuit design template is connected like this:

| LED Port    | Connect To                       |
| ----------- | -------------------------------- |
| Anode (+)   | **Pin 8 through 220 Ω resistor** |
| Cathode (-) | **GND**                          |

<img width="1686" height="912" alt="image" src="https://github.com/user-attachments/assets/6c6d33ad-5c8c-417b-9cfd-1efba5806329" />

---

## Basic LED Control

We can turn an LED on by setting its pin to **HIGH**.

```cpp
digitalWrite(8, HIGH);
```

We can turn the LED off by setting the same pin to **LOW**.

```cpp
digitalWrite(8, LOW);
```

In TinkerCAD Blocks, this is done using the **set pin** block.

<img width="392" height="108" alt="image" src="https://github.com/user-attachments/assets/1ecee3e8-8785-4207-885f-63d920c7e515" />

* `HIGH` → Turns the LED **ON**
* `LOW` → Turns the LED **OFF**

---

## Part 2: Making an LED Blink

Remember `delay()` from the servo lesson?

We can combine `digitalWrite()` and `delay()` to make an LED blink.

```cpp
digitalWrite(8, HIGH);
delay(1000);

digitalWrite(8, LOW);
delay(1000);
```

### What is this code doing?

First, we set pin 8 to **HIGH**, which turns the LED on.

Then, we wait for `1000` milliseconds, or **1 second**.

Next, we set pin 8 to **LOW**, which turns the LED off.

Finally, we wait another second.

Because this code is inside the Arduino's `loop()`, the process repeats again and again!

---

## What Does Changing `delay()` Do?

The `delay()` controls how long the LED stays in each state.

* `delay(2000)` → Wait **2 seconds**
* `delay(1000)` → Wait **1 second**
* `delay(500)` → Wait **0.5 seconds**
* `delay(100)` → Wait **0.1 seconds**

A smaller delay will make the LED blink **faster**.

A larger delay will make the LED blink **slower**.

---

## Student Challenges

Try modifying the code to explore different behaviors:

* Make the LED blink faster using `delay(500)`.
* Make the LED blink very quickly using `delay(100)`.
* Make the LED stay ON for 2 seconds but OFF for only 0.5 seconds.
* Bonus: Add a second LED and make the two LEDs alternate.

Don't stress about perfection — explore and observe!

---

## Quick Reference Table for Arduino Text Code

| Concept          | Function                | Description                     |
| ---------------- | ----------------------- | ------------------------------- |
| Set output       | `pinMode(8, OUTPUT)`    | Allows pin 8 to control the LED |
| LED ON           | `digitalWrite(8, HIGH)` | Turns the LED on                |
| LED OFF          | `digitalWrite(8, LOW)`  | Turns the LED off               |
| Wait 1 second    | `delay(1000)`           | Waits 1000 milliseconds         |
| Wait 0.5 seconds | `delay(500)`            | Waits 500 milliseconds          |

---
