# ⚡ ECE/IEEE Summer Workshop: Introduction to Arduino & Circuits with TinkerCAD

Welcome to our self-paced **Arduino and electronics workshop using TinkerCAD!**

In this workshop, you'll learn how electronic circuits work by building and programming your own circuits — completely online.

**No previous electronics or programming experience is required!**

We'll start with the basics and gradually work our way toward controlling motors, lights, buttons, and sensors with an Arduino.

---

## 🌟 What Are We Learning?

Look around you and you'll find electronics everywhere.

Your phone, computer, game controller, microwave, car, and even your washing machine contain electronic circuits that allow them to sense information, make decisions, and control things.

But how do these devices actually work?

At their core, many electronic systems follow a simple pattern:

**INPUT → PROCESS → OUTPUT**

For example:

**Push Button → Arduino → LED**

The **button** provides information.

The **Arduino** processes that information.

The **LED** responds by turning on or off.

Throughout this workshop, we'll build circuits that follow this same basic idea.

---

# 💻 What Is TinkerCAD?

**TinkerCAD Circuits** is an online simulator that allows us to build and test electronic circuits without needing physical components.

Instead of physically plugging wires into an Arduino, we can build everything on the computer.

<img width="1810" height="764" alt="image" src="https://github.com/user-attachments/assets/eac0990d-dc1b-472b-b094-71c15debd3e1" />

TinkerCAD allows us to:

* Place electronic components
* Connect components using wires
* Program an Arduino
* Start and stop a simulation
* See how the circuit behaves
* Experiment without worrying about damaging real components

Think of TinkerCAD as a **virtual electronics laboratory**.

If you make a mistake, that's okay!

You can change the circuit, restart the simulation, and try again.

> 💡 **Throughout this workshop, don't be afraid to experiment!** Changing things and observing what happens is one of the best ways to learn electronics.

---

# 🔌 What Is a Circuit?

Before we start building, let's understand what a **circuit** actually is.

A circuit is a path that allows **electric current** to flow.

For current to continuously flow, there generally needs to be a **complete path**.

A very simple circuit might contain:

**Power → Component → Ground**

For example:

**5V → Resistor → LED → GND**

<img width="2162" height="852" alt="image" src="https://github.com/user-attachments/assets/b05d4905-8a45-4afe-b45c-36bb767d2a91" />

If the path is complete, current can flow through the circuit.

If the path is broken, current cannot continuously flow through it.

Think about a circular racetrack.

If the track forms a complete loop, the cars can keep moving around it.

If part of the track is missing, the cars can't complete the path.

A circuit works in a similar way.

---

# ⚡ What Is Voltage?

You'll see labels like these throughout the workshop:

**5V**

**3.3V**

**GND**

Voltage is the **electrical potential difference** between two points.

For now, you can think of voltage as the **electrical push** that can cause current to flow through a circuit.

A useful analogy is water pressure.

* **Voltage** → Similar to water pressure
* **Current** → Similar to the amount of water flowing
* **Wire** → Similar to the pipe carrying the water

Higher pressure can push water through a pipe.

Similarly, a voltage difference can cause electric current to flow through a circuit.

> 💡 This analogy isn't perfect, but it is a useful way to begin thinking about electricity.

---

# ⏚ What Is Ground (GND)?

You'll see **GND** constantly when working with Arduino circuits.

GND stands for **Ground**.

Ground is the point we use as the **0-volt reference** for our circuit.

If an Arduino pin is at 5V relative to GND, there is a 5-volt difference between those two points.

Many simple Arduino circuits create a path like:

**Arduino Pin / 5V → Component → GND**

<img width="166" height="248" alt="image" src="https://github.com/user-attachments/assets/ee43d25b-f5e6-419d-9b24-a25f8f02f1ce" />

You can think of GND as the circuit's **electrical reference point** and often part of the return path for current.

---

# 🧠 What Is an Arduino?

The most important component we'll use is the **Arduino Uno**.

<img width="1142" height="904" alt="image" src="https://github.com/user-attachments/assets/abe09f79-e13d-41a4-9a08-9763b276ed88" />

An Arduino is a small **microcontroller development board**.

A microcontroller is essentially a tiny computer designed to interact with electronic components.

We can give the Arduino instructions that tell it things like:

* Turn an LED on.
* Check if a button was pressed.
* Measure the amount of light in a room.
* Measure the distance to an object.
* Move a motor.
* Rotate a servo to a certain angle.

The Arduino repeatedly follows the instructions we give it.

This allows it to connect **programming** with the **physical world**.

---

## 🧠 Think of the Arduino as the Brain

A useful way to think about an Arduino is as the **brain of the circuit**.

Imagine this circuit:

**Button → Arduino → LED**

The button is an **input**.

The Arduino reads the button and makes a **decision**.

The LED is an **output**.

For example:

**IF button is pressed → Turn LED ON**

We can also use sensors:

**Light Sensor → Arduino → LED**

The Arduino could measure the amount of light and automatically turn on the LED when the room gets dark.

This ability to **sense → decide → respond** is what makes microcontrollers so useful.

---

# 🔢 Understanding Arduino Pins

Look around the edges of the Arduino Uno and you'll see many small connections called **pins**.

<img width="772" height="206" alt="image" src="https://github.com/user-attachments/assets/cd552783-bf25-42b1-863c-047dc0cc0e2d" />

Pins allow the Arduino to communicate with other electronic components.

Some pins can send signals.

Some pins can receive signals.

Some can do both depending on how we program them.

---

## Digital Pins

The pins numbered:

**0, 1, 2, 3, 4...**

are called **digital pins**.

Digital signals usually have two states:

**HIGH** or **LOW**

For a typical Arduino Uno:

**HIGH ≈ 5V**

**LOW ≈ 0V**

You can think of this approximately like:

**HIGH → ON**

**LOW → OFF**

For example, the Arduino could send HIGH to an LED:

```cpp
digitalWrite(8, HIGH);
```

The Arduino is telling **pin 8** to output a HIGH signal.

If the circuit is wired correctly, this can turn the LED on.

---

## Analog Inputs

You'll also see pins labeled:

**A0, A1, A2, A3, A4, A5**

These are **analog input pins**.

Instead of only detecting HIGH or LOW, analog inputs can measure a range of voltages.

For example, a photoresistor circuit can produce different voltages depending on the amount of light.

The Arduino can measure this and turn it into a number.

This allows us to measure things that aren't simply ON or OFF.

---

# 📶 What Do We Mean by a "Signal"?

Throughout these lessons, you'll see the word **signal**.

A signal is an electrical quantity that carries information.

For example, imagine an Arduino pin switching between:

**0V → 5V → 0V → 5V**

Those changing voltage levels can communicate information to another component.

A simple signal might mean:

**5V → Turn ON**

**0V → Turn OFF**

Other signals can be more complicated and can communicate measurements, timing, speed, position, or other information.

So when we say:

> "The Arduino sends a signal to the component"

we usually mean that the Arduino is **changing an electrical voltage on one of its pins in a controlled way**.

---

# 🧵 What Do Wires Do?

<img width="882" height="332" alt="image" src="https://github.com/user-attachments/assets/bc1762d8-2e24-457a-bc2b-086af8bd64a9" />

Wires create **electrical connections** between different points in our circuit.

If you connect an Arduino pin to an LED using a wire, those two points become electrically connected.

Wires can carry:

* Power
* Ground connections
* Input signals
* Output signals

In TinkerCAD, you'll create these connections by clicking one component pin and connecting it to another point.

### Wire Colors

The color of a wire **does not change how electricity flows**.

However, using different colors makes circuits much easier to understand.

A common convention is:

| Wire Color   | Usually Used For |
| ------------ | ---------------- |
| Red          | Power            |
| Black        | Ground           |
| Other Colors | Signals          |

> 💡 Using consistent wire colors will make complicated circuits much easier to troubleshoot!

---

# 🍞 What Is a Breadboard?

You'll also see something called a **breadboard**.

<img width="678" height="450" alt="image" src="https://github.com/user-attachments/assets/e224cf2f-6776-464a-8c4f-e1a3d736df84" />

A breadboard allows us to connect electronic components **without soldering them together**.

Instead of permanently attaching components, we can simply plug components and wires into holes.

This makes breadboards perfect for:

* Learning electronics
* Testing circuits
* Building prototypes
* Quickly changing connections

But there is one important thing to understand:

**The holes aren't all separate!**

Many holes are already electrically connected **inside the breadboard**.

---

## How Is a Breadboard Connected?

In the main center area, holes are typically connected in small groups.

A simplified section might look like:

```text
A  B  C  D  E

●--●--●--●--●

●--●--●--●--●

●--●--●--●--●
```

Each horizontal group of five holes shown above is electrically connected.

That means if you connect a wire to one hole, a component placed in another hole in the **same connected group** is connected to that wire.

<img width="1088" height="536" alt="image" src="https://github.com/user-attachments/assets/dff18ad3-2acc-496d-a380-1b514a614e5d" />

This lets us connect several components together without twisting or soldering wires.

---

## The Middle Gap

Most breadboards also have a gap running down the center.

```text
A B C D E     F G H I J
● ● ● ● ●     ● ● ● ● ●
● ● ● ● ●     ● ● ● ● ●
● ● ● ● ●     ● ● ● ● ●
        ↑
      GAP
```

Connections do **not** cross this center gap.

This gap is useful when working with certain electronic components and integrated circuits.

---

## Power Rails

Many breadboards also have long rows along the sides called **power rails**.

They are commonly marked:

**+**

and

**−**

We can connect:

**Arduino 5V → + rail**

and:

**Arduino GND → − rail**

Now components across the breadboard can easily access power and ground.

<img width="1650" height="184" alt="image" src="https://github.com/user-attachments/assets/8d548524-9069-4528-bc7d-4cfe5fbba9cb" />

> ⚠️ Always look carefully at how the breadboard connections are arranged. Two holes that look close together are not necessarily electrically connected!

---

# 💡 Example: Turning On an LED

Let's put these ideas together.

Imagine we connect:

**Arduino Pin 8 → Resistor → LED → GND**

<img width="1192" height="1216" alt="image" src="https://github.com/user-attachments/assets/64519791-9454-4648-8420-62ff80182161" />

The Arduino can set pin 8 to HIGH:

```cpp
digitalWrite(8, HIGH);
```

Now pin 8 is approximately **5V relative to GND**.

There is a voltage difference across the circuit, so current can flow through the resistor and LED toward GND.

The LED turns on!

If we instead write:

```cpp
digitalWrite(8, LOW);
```

pin 8 is approximately **0V relative to GND**.

There is now approximately no voltage difference driving current through that LED path, so the LED turns off.

This simple example demonstrates the main idea behind many of the circuits we'll build:

**Arduino creates electrical signals → Components respond**

---

# 💻 How Does Programming Fit In?

The Arduino needs instructions telling it what to do.

These instructions are called **code**.

In TinkerCAD, we can program the Arduino using visual **Blocks**.

<img width="894" height="780" alt="image" src="https://github.com/user-attachments/assets/4513435b-78cd-4fd6-a37e-0ee6f81191dc" />

Instead of typing every command, we can drag blocks together.

For example, we might create instructions that say:

**Set pin 8 to HIGH**

**Wait 1 second**

**Set pin 8 to LOW**

**Wait 1 second**

The Arduino repeatedly follows those instructions, causing our LED to blink.

As we go through the workshop, we'll also show what many of these blocks look like as normal **Arduino text code**.

Don't worry if the text code looks confusing at first!

You'll learn what each command means as we use it.

---

# 🔁 How Does an Arduino Program Run?

Arduino programs generally contain two important sections:

```cpp
void setup() {

}
```

and:

```cpp
void loop() {

}
```

### `setup()`

Code inside `setup()` runs **once** when the Arduino starts.

We usually use this to prepare our circuit.

For example:

```cpp
pinMode(8, OUTPUT);
```

This tells the Arduino that pin 8 will be used as an **output**.

### `loop()`

Code inside `loop()` runs **again and again**.

Once Arduino reaches the bottom of `loop()`, it goes back to the top and starts again.

For example:

```cpp
void loop() {

    digitalWrite(8, HIGH);
    delay(1000);

    digitalWrite(8, LOW);
    delay(1000);

}
```

This program continuously turns an LED on and off.

Don't worry about memorizing any of this yet!

You'll practice these commands throughout the lessons.

---

# 🚀 Workshop Overview

Throughout this workshop, you'll build several circuits that introduce different electronics and programming concepts.

You'll experiment with:

* 💡 **LEDs** — Control lights using Arduino outputs
* 🔘 **Push Buttons** — Give the Arduino a digital input
* 🔁 **Servo Motors** — Control precise movement and angles
* ⚙️ **DC Motors** — Control continuous motion and speed
* ☀️ **Photoresistors** — Measure changing light levels
* 📡 **Ultrasonic Sensors** — Measure the distance to objects

Each lesson introduces a new component while building on concepts from previous lessons.

---

# 📚 Workshop Lessons

| Lesson | Topic             | What You'll Learn                               |
| ------ | ----------------- | ----------------------------------------------- |
| 1      | LED Basics        | Outputs, HIGH/LOW, and blinking                 |
| 2      | Servo Motor       | Angles, movement, `delay()`, and loops          |
| 3      | Push Button       | Inputs, `digitalRead()`, and `if` statements    |
| 4      | DC Motor          | Motor control, speed, and PWM                   |
| 5      | Photoresistor     | Analog inputs, variables, and light sensing     |
| 6      | Ultrasonic Sensor | Distance sensing, Serial Monitor, and decisions |

---

# 🛠️ How to Use These Lessons

Each lesson is **self-paced**.

You don't need to rush!

For each activity:

1. Read the explanation of the component.
2. Look at the provided circuit in TinkerCAD.
3. Check how the circuit is wired.
4. Build or modify the block code.
5. Click **Start Simulation**.
6. Observe what happens.
7. Complete the Student Challenges.

If your circuit doesn't work the first time, **that's completely normal!**

Debugging — figuring out why something doesn't work — is an important part of engineering.

Check:

* Are your wires connected to the correct pins?
* Is power connected correctly?
* Is GND connected?
* Are your components facing the correct direction?
* Are the correct pin numbers selected in your code?
* Did you start the simulation?

Change one thing at a time and test again.

---

# 🧠 Three Ideas to Remember

Before beginning Lesson 1, remember these three ideas:

### 1. A Circuit Needs Connections

Components must be electrically connected correctly for current and signals to travel through the circuit.

### 2. The Arduino Is the Controller

The Arduino follows your program and uses its pins to **read inputs** and **control outputs**.

### 3. Inputs → Decisions → Outputs

Many electronic systems can be understood using:

**INPUT → PROCESS → OUTPUT**

For example:

**Button → Arduino → LED**

or:

**Photoresistor → Arduino → Motor**

or:

**Ultrasonic Sensor → Arduino → LED**

Once you understand this pattern, even much more complicated electronic systems become easier to understand.

---

# 🎯 Ready to Begin?

You now know the basic pieces we'll be using:

**Arduino → The controller**

**Breadboard → Helps us connect components**

**Wires → Create electrical connections**

**5V → Provides electrical potential**

**GND → Our 0V reference**

**Inputs → Give information to the Arduino**

**Outputs → Are controlled by the Arduino**

You do **not** need to memorize everything on this page.

You'll practice these ideas throughout the workshop.

The most important thing is to **experiment, ask questions, and observe what happens.**

Now you're ready to build your first circuit!

---
