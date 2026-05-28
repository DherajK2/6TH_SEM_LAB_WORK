# IoT Lab – Experiment: Ultrasonic Sensor LED Control

---

## Aim

To use an **Arduino Uno**, an **ultrasonic sensor**, and an **LED** to measure distance.  
The LED will blink if an object comes closer than **10 cm**, based on the sensor's duration and distance calculation.

---

## Materials Required

- Arduino Uno  
- Ultrasonic sensor (HC-SR04)  
- LED  
- Resistor (220Ω)  
- Breadboard  
- Jumper wires  
- USB cable for Arduino  
- Computer with Arduino IDE  

---

## Construction

**LED Connection:**  
- Connect the **long leg (positive)** of LED to **Digital Pin 3**.  
- Connect the **short leg (negative)** to a **resistor**.  
- Connect the other side of the resistor to **GND**.

**Ultrasonic Sensor Connection:**  
- **VCC → 5V**  
- **Trig Pin → Digital Pin 9**  
- **Echo Pin → Digital Pin 10**  
- **GND → GND**

**Circuit Layout:** Use a breadboard to connect all components neatly with jumper wires.

---

## Source Code

```cpp
long duration;
float distance;

int trigPin = 9;
int echoPin = 10;
int ledPin = 3;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  distance = duration * 0.034 / 2;

  if(distance < 10) {
    Serial.print("Duration: ");
    Serial.print(duration);
    Serial.print("  Distance: ");
    Serial.println(distance);

    digitalWrite(ledPin, HIGH);
    delay(200);
    digitalWrite(ledPin, LOW);
    delay(200);
  }
  else {
    digitalWrite(ledPin, LOW);
  }
}

```

## How to Run

1. **Connect the Hardware:**  
   - Connect the LED and ultrasonic sensor to the Arduino Uno as described in the construction section.  
   - Connect the Arduino to your computer using a **USB cable**.

2. **Open Arduino IDE:**  
   - Launch the Arduino IDE on your computer.  
   - Open a new sketch or paste the provided source code.

3. **Select Board and Port:**  
   - Go to **Tools → Board → Arduino Uno**.  
   - Go to **Tools → Port → COMx** (where your Arduino is connected).

4. **Upload the Code:**  
   - Click the **Upload** button (→) in Arduino IDE.  
   - Wait until the IDE shows **“Done uploading”**.

5. **Monitor the Output:**  
   - Open the **Serial Monitor** (**Tools → Serial Monitor**).  
   - Set the baud rate to **9600**.  
   - Observe **duration** and **distance values** printed in real-time.  
   - Move an object closer than **10 cm** to the ultrasonic sensor.  
   - The LED will **blink** when the object is within 10 cm.

---

## Output

**Serial Monitor Example:**  
```
    Duration: 590  Distance: 10.03
    Duration: 580  Distance: 9.86
    Duration: 575  Distance: 9.77
```
---
**LED Behavior:**  
- LED remains **OFF** when object > 10 cm.  
- LED **blinks** when object < 10 cm.  
- Observed distance readings update continuously as the object moves closer or farther.

---

## Explanation of the Code

1. **Pins Setup:**  
   - `trigPin` triggers the ultrasonic pulse.  
   - `echoPin` reads the returning signal.  
   - `ledPin` controls the LED.

2. **Measuring Distance:**  
   - Sensor sends a pulse via `trigPin`.  
   - `pulseIn()` measures the **duration** of the returning pulse on `echoPin`.  
   - Distance is calculated using: `distance = duration * 0.034 / 2;`  
     (0.034 cm/μs is speed of sound; divide by 2 for the round trip)

3. **LED Control:**  
   - If `distance < 10 cm`, LED blinks every 200 ms.  
   - Otherwise, LED stays OFF.

4. **Serial Monitor:**  
   - Prints `Duration` and `Distance` for real-time monitoring.

---

## Viva Questions

1. **What is the function of `pulseIn()`?**  
   Measures the duration of the high pulse on the echo pin.

2. **Why divide duration by 2 in distance calculation?**  
   Because the sound travels **to the object and back**; divide by 2 for one-way distance.

3. **What speed of sound is used?**  
   0.034 cm/μs (centimeters per microsecond)

4. **Which pin triggers the ultrasonic sensor?**  
   Digital Pin 9

5. **How is the LED controlled?**  
   It blinks when object < 10 cm, otherwise stays OFF.

6. **Can the sensor detect distances > 10 cm?**  
   Yes, but LED will not blink; it only reacts to distances < 10 cm.

7. **Why use a resistor with the LED?**  
   To limit current and prevent LED burnout.

---

## Observations

- LED blinks faster if an object moves closer.  
- Serial Monitor shows real-time **duration** and **distance values**.  

---

## Result

- Successfully controlled the LED using an ultrasonic sensor.  
- Distance measurements matched expected values.  
- LED blinked as intended when an object came within **10 cm** of the sensor.
