# IoT Lab – Experiment: Vibration Sensor LED & Buzzer Control

---

## Aim

To use an **Arduino Uno**, an **vibration sensor**, **LED** and a **buzzer** to detect vibrations.
When vibration is detected, the **LED and buzzer will turn ON.**, 

---

## Materials Required

- Arduino Uno  
- Vibration sensor (SW420)  
- LED  
- Resistor (220Ω)  
- Breadboard  
- Jumper wires  
- USB cable for Arduino  
- Computer with Arduino IDE  

---

## Construction

**LED Connection:**  
- Connect the **long leg (positive)** of LED to **Digital Pin 7**.  
- Connect the **short leg (negative)** to a **resistor**.  
- Connect the other side of the resistor to **GND**.

**Vibration Sensor Connection:**  
- **VCC → 5V**
- **GND → GND**
- **DO (Output) → Digital Pin 2**  



**Circuit Layout:** Use a breadboard to connect all components neatly with jumper wires.

---

## Source Code

```cpp
const int vibPin = 2;
const int ledPin = 7;
const int buzzPin = 8;

void setup() {
  pinMode(vibPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int vibState = digitalRead(vibPin);

  if (vibState == LOW) {
    Serial.println("Vibration Detected");

    digitalWrite(ledPin, HIGH);
    digitalWrite(buzzPin, HIGH);

    delay(500);
  } 
  else {
    digitalWrite(ledPin, LOW);
    digitalWrite(buzzPin, LOW);
  }

  delay(50);
}
```

## How to Run

1. **Connect the Hardware:**  
   - Connect vibration sensor, LED, and buzzer as described.
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
   
   - Tap or shake the **sensor** → LED & buzzer activate
   - The LED will **blink** and simultaneously even the **buzzer** too

---

## Output

**Serial Monitor Example:**  
```
   Vibration Detected
Vibration Detected
```
---
**LED Behavior:**  
- LED,Buzzer remains **OFF** when no vibration is detected.
- LED **blinks** and Buzzer sounds whenever vibration is detected.


---

## Explanation of the Code

1. **Pins Setup:**  
   - `vibPin` reads vibration signal
   - `ledPin` controls the LED.
   - `buzzPin` controls the buzzer

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

1. **`What is a vibration sensor?`?**  
   A sensor that detects motion, shock, or vibration and converts it into an electrical signal.

2. **Which pin is used for vibration detection?**  
   Digital Pin 2

3. **Why is digitalRead() used?**  
  To read HIGH/LOW signal from the sensor.

4. **What happens when vibration is detected?**  
   LED and buzzer turn ON.

5. **How is the LED controlled?**  
   It blinks when object < 10 cm, otherwise stays OFF.

6. **What type of signal does the sensor give?**  
   Digital (HIGH/LOW)

7. **Can sensitivity be adjusted?**  
   Yes, using the potentiometer on the sensor module.

---

## Observations

- LED and buzzer respond instantly to vibration.
- Sensor detects even small movements or taps.
- Serial monitor confirms detection events.

---

## Result

- Successfully implemented vibration detection using Arduino.
- LED and buzzer responded correctly to vibrations.
- System worked as expected based on sensor input.
