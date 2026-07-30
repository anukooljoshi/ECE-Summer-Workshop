# Lesson 6 — Ultrasonic Sensor

## Objectives

* Understand how an **ultrasonic sensor** measures distance using sound waves.
* Learn how the **Trigger** and **Echo** pins work.
* Display distance measurements on the **Serial Monitor**.
* Store sensor measurements inside a variable.
* Use an **`if` statement** to detect nearby objects.

---

## Part 1: What Is an Ultrasonic Sensor?

<img width="500" height="268" alt="image" src="https://github.com/user-attachments/assets/e8c86b76-aa77-4b8f-9b4b-add5b7c4ceb9" />

The **HC-SR04 ultrasonic sensor** is a distance sensor that uses sound waves to determine how far away an object is.

It works by:

* Sending out a **high-frequency sound pulse**
* Waiting for the sound to bounce off an object
* Listening for the returning **echo**
* Measuring how long the sound took to travel

The sound is too high-pitched for humans to hear, but the sensor can detect it.

Another way to think about it: an ultrasonic sensor works like a **bat using echolocation**.

A bat sends out sound and listens for the echo to determine how far away objects are.

Our sensor does the same thing!

---

## How Does It Measure Distance?

The sensor measures something called **time-of-flight**.

This means it measures how long the sound takes to travel:

**Sensor → Object → Sensor**

Sound travels through air at approximately **343 meters per second**.

If the echo takes a long time to return, the object is farther away.

If the echo returns quickly, the object is closer.

Because the sound has to travel **to the object and back**, we divide the total travel distance by 2.

---

## Pin Wiring Table

<img width="540" height="357" alt="image" src="https://github.com/user-attachments/assets/4c226e52-1172-4454-a67d-2036745b1e43" />

In TinkerCAD, ensure that the circuit design template is connected like this:

| HC-SR04 Pin  | Connect To |
| ------------ | ---------- |
| VCC / Power  | **5V**     |
| GND / Ground | **GND**    |
| TRIG         | **Pin 4**  |
| ECHO         | **Pin 5**  |

The **TRIG** pin sends the ultrasonic pulse.

The **ECHO** pin receives the returning pulse.

---

## Part 2: Reading Distance in TinkerCAD

In TinkerCAD, we can use the ultrasonic distance block from the **Input** tab.

<img width="963" height="157" alt="image" src="https://github.com/user-attachments/assets/e4b21970-4566-4dd0-9223-452711850eda" />

This block automatically performs the ultrasonic measurement and gives us a distance reading.

For this activity, make sure:

* Trigger pin is **4**
* Echo pin is **5**
* Distance is measured in **centimeters**

This makes measuring distance much easier because TinkerCAD handles the Trigger and Echo signals for us.

---

## Part 3: Storing the Distance in a Variable

Remember variables from the photoresistor lesson?

A variable is like a **labeled box that stores information**.

Create a variable called:

`distance`

<img width="1192" height="114" alt="image" src="https://github.com/user-attachments/assets/1221c34c-d46b-4ab3-ae61-5232b0494cb3" />

We can store the sensor measurement inside this variable.

The idea is:

**Measure distance → Store measurement in `distance`**

Every time the program repeats, the Arduino can take a new measurement and update the value stored inside `distance`.

---

## Part 4: Using the Serial Monitor

Now we can print our `distance` variable to the **Serial Monitor**.

<img width="1254" height="329" alt="image" src="https://github.com/user-attachments/assets/37091f79-5b0d-4d04-9ece-380c6ab22425" />

The **Serial Monitor** allows the Arduino to display information on the computer.

For example, in Arduino text code:

```cpp
Serial.println(distance);
```

This tells the Arduino:

> Print the current value stored inside `distance`.

### How to Open the Serial Monitor

* Click the **Code** button in TinkerCAD.
* Start the simulation.
* Find the **Serial Monitor** below the code area.
* Watch the distance measurements appear.

The numbers should automatically update as the measured distance changes.

---

## Part 5: Testing the Sensor

To test the ultrasonic sensor in TinkerCAD, start the simulation and click on the sensor.

<img width="795" height="744" alt="image" src="https://github.com/user-attachments/assets/8c2ffadb-7257-4e94-a02f-750b34c4a068" />

A simulated object will appear in front of the sensor.

Move the object closer to or farther away from the sensor.

Watch what happens to the value in the **Serial Monitor**.

You should notice:

* Moving the object **closer** → Smaller distance
* Moving the object **farther away** → Larger distance

Try placing the object at several different distances and compare the readings.

---

## Part 6: What Is an `if` Statement?

Remember the `if` statement from the push button lesson?

An `if` statement allows the Arduino to **make a decision**.

For example:

> **IF** an object is closer than 10 cm, display a warning.

<img width="1216" height="422" alt="image" src="https://github.com/user-attachments/assets/e57ab759-44f2-4477-b6bd-7bc8d26ccec4" />

In Arduino text code:

```cpp
if (distance < 10) {
    Serial.println("Object too close!");
}
```

This code checks:

```cpp
distance < 10
```

If the condition is **true**, the code inside the `if` statement runs.

If the object is farther than 10 cm away, the code inside the `if` statement does not run.

---

## Adding an `else`

We can also make something happen when the object is not close.

```cpp
if (distance < 10) {
    Serial.println("Object Detected!");
}
else {
    Serial.println("All Clear!");
}
```

Now our Arduino makes one of two decisions:

* Distance below 10 cm → **Object Detected!**
* Distance 10 cm or greater → **All Clear!**

This allows the Arduino to respond differently depending on how close an object is to the sensor.

---

## Part 7: How Does the Sensor Actually Work?

TinkerCAD's ultrasonic sensor block makes measuring distance easy, but let's take a quick look at what is happening behind the scenes.

First, the Arduino sends a very short signal through the **Trigger** pin.

```cpp
digitalWrite(4, LOW);
delayMicroseconds(2);

digitalWrite(4, HIGH);
delayMicroseconds(10);

digitalWrite(4, LOW);
```

The sensor needs a **10 microsecond pulse** to begin an ultrasonic measurement.

A microsecond is extremely small:

**1 second = 1,000,000 microseconds**

After receiving this signal, the sensor sends out its ultrasonic sound wave.

---

## Measuring the Echo

After sending the ultrasonic pulse, we measure how long the Echo pin stays HIGH.

```cpp
duration = pulseIn(5, HIGH);
```

The function:

```cpp
pulseIn()
```

measures how long a signal remains HIGH or LOW.

For the ultrasonic sensor, this gives us the **round-trip travel time** of the sound wave.

---

## Calculating Distance

Once we know the travel time, we can calculate the distance.

One common formula for centimeters is:

```cpp
distance = duration * 0.0343 / 2;
```

The `0.0343` comes from the approximate speed of sound in **centimeters per microsecond**.

### Why do we divide by 2?

Remember that the sound travels:

**Sensor → Object → Sensor**

But we only want the distance:

**Sensor → Object**

So we divide the total travel distance by **2**.

---

## Student Challenges

Try modifying the code to explore different behaviors:

* Display `"Object Detected!"` when something is closer than **20 cm**.
* Display `"All Clear!"` when the object is farther away.
* Change the detection distance from 20 cm to another value.
* Add an LED that turns on when an object gets too close.
* Change the LED warning distance and observe what happens.
* Bonus: Make an LED blink faster as the object gets closer.

Don't stress about perfection — explore and observe!

---

## Full Example Code

```cpp
int trigPin = 4;
int echoPin = 5;

long duration;
float distance;

void setup() {
    Serial.begin(9600);

    pinMode(trigPin, OUTPUT);
    pinMode(echoPin, INPUT);
}

void loop() {

    // Send ultrasonic trigger pulse
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);

    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);

    digitalWrite(trigPin, LOW);

    // Measure echo travel time
    duration = pulseIn(echoPin, HIGH);

    // Convert travel time to distance in centimeters
    distance = duration * 0.0343 / 2;

    // Print distance
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");

    // Detect nearby object
    if (distance < 10) {
        Serial.println("Object too close!");
    }
    else {
        Serial.println("All Clear!");
    }

    delay(500);
}
```

---

## Quick Reference Table for Arduino Text Code

| Concept        | Function              | Description                                  |
| -------------- | --------------------- | -------------------------------------------- |
| Set pin mode   | `pinMode()`           | Sets a pin as an input or output             |
| Trigger signal | `digitalWrite()`      | Sends HIGH or LOW through the Trigger pin    |
| Tiny delay     | `delayMicroseconds()` | Waits for a number of microseconds           |
| Measure echo   | `pulseIn()`           | Measures how long the Echo signal stays HIGH |
| Store distance | `float distance`      | Stores the calculated distance               |
| Serial output  | `Serial.print()`      | Displays text or measurements                |
| Conditional    | `if (...)`            | Runs code when a condition is true           |
| Alternative    | `else`                | Runs code when the condition is false        |

---
