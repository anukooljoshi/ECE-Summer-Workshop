# Lesson 4 — DC Motor

## Objectives

* Understand what a DC motor is and how it works.
* Understand the difference between a DC motor and a servo motor.
* Learn how to turn a DC motor ON and OFF in TinkerCAD.
* Learn how PWM can control motor speed.
* Use a `for` loop to gradually change motor speed.

---

## Part 1: What Is a DC Motor?

<img width="290" height="234" alt="image" src="https://github.com/user-attachments/assets/5b1b8ce3-813a-4dee-96de-34a2ab77932d" />

A **DC motor** is a motor that continuously spins when electrical power is applied.

This is different from the **servo motor** we used in Lesson 1.

Remember:

A servo motor rotates to a **specific angle**.

A DC motor **continuously spins**.

Another way to think about it:

A servo motor is like a **steering wheel** because we care about its exact angle.

A DC motor is like a **fan** because we care about how fast and in what direction it spins.

DC motors are commonly used for the **wheels of robots**, including the Keyestudio 4WD Robot Car.

---

## Part 2: Connecting a DC Motor

A DC motor can require more current than an Arduino output pin can safely provide.

Because of this, we should **not connect the motor directly to an Arduino output pin**.

Instead, we use a component such as a **transistor or motor driver**.


The transistor allows a small Arduino signal to control the larger amount of current needed by the motor.

---

## Pin Wiring Table

In TinkerCAD, ensure that the provided circuit design template is connected like this:

| Component     | Connect To                 |
| ------------- | -------------------------- |
| Motor Control | **Pin 9**                  |
| Motor         | **Motor Power Circuit**    |
| Transistor    | **Controls Motor Current** |
| Ground        | **GND**                    |

The provided TinkerCAD design should already contain the necessary motor-control components.

---

## Basic Motor Control

We can turn the motor ON using:

```cpp
digitalWrite(9, HIGH);
```

We can turn the motor OFF using:

```cpp
digitalWrite(9, LOW);
```

For example:

```cpp
digitalWrite(9, HIGH);
delay(2000);

digitalWrite(9, LOW);
delay(1000);
```

### What is this code doing?

First, the motor turns ON.

The Arduino waits for **2 seconds**.

Then, the motor turns OFF.

The Arduino waits for **1 second**.

Because this is inside `loop()`, the process repeats.

---

## Part 3: Controlling Motor Speed

What if we don't want our motor running at full speed?

Arduino can control the average power sent to a motor using something called **PWM**, or **Pulse Width Modulation**.

PWM rapidly switches an output between ON and OFF.

[INSERT PWM / TINKERCAD BLOCK IMAGE HERE]

Instead of only using HIGH and LOW, we can use values between:

**0 → 255**

For example:

```cpp
analogWrite(9, 0);
```

means the motor receives no PWM output.

```cpp
analogWrite(9, 128);
```

gives approximately a 50% duty cycle.

```cpp
analogWrite(9, 255);
```

gives a 100% duty cycle.

So we can think of it approximately like this:

* `0` → Motor OFF
* `64` → Low power
* `128` → Medium power
* `192` → High power
* `255` → Full power

---

## Part 4: Using a `for` Loop

Remember the `for` loop from the servo motor lesson?

Instead of gradually changing the **angle** of a servo, we can gradually change the **speed** of our DC motor.

```cpp
for (int speed = 0; speed <= 255; speed++) {
    analogWrite(9, speed);
    delay(20);
}
```

### What is this code doing?

We create a variable called `speed`.

It starts at **0**.

Every time the loop repeats, `speed` increases by **1**.

The motor therefore receives:

`0 → 1 → 2 → 3 → ... → 255`

This causes the motor to gradually increase from stopped toward full power.

The `delay(20)` gives us enough time to observe the gradual change.

---

## Student Challenges

Try modifying the code to explore different behaviors:

* Make the motor run at approximately half power.
* Make the motor run at full power for 2 seconds and then stop.
* Make the motor gradually speed up from 0 to 255.
* Make the motor gradually speed up faster by changing `delay(20)`.
* Bonus: Make the motor gradually speed up **and then slow back down**.

Don't stress about perfection — explore and observe!

---

## Quick Reference Table for Arduino Text Code

| Concept       | Function                | Description                         |
| ------------- | ----------------------- | ----------------------------------- |
| Motor ON      | `digitalWrite(9, HIGH)` | Sends full output to motor control  |
| Motor OFF     | `digitalWrite(9, LOW)`  | Turns motor control off             |
| Speed control | `analogWrite(9, value)` | Sends PWM from 0–255                |
| Half power    | `analogWrite(9, 128)`   | Approximately 50% duty cycle        |
| Full power    | `analogWrite(9, 255)`   | 100% duty cycle                     |
| For loop      | `for (...)`             | Repeats code while changing a value |

---
