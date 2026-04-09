# IoT Lab – Experiment: LDR Sensor LED Control

---

## Aim

To use an **Arduino Uno** and an **LDR (Light Dependent Resistor)** to detect light intensity.  
The LED will turn ON or OFF based on a **threshold value (500)**.

---

## Materials Required

- Arduino Uno  
- LDR (Light Dependent Resistor)  
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

**LDR Connection:**  
- One end of LDR → **5V**  
- Other end → **A0 (Analog Pin)**  
- Connect a resistor from A0 to **GND** (voltage divider)

**Circuit Layout:**  
Use a breadboard and jumper wires for proper connections.

---

## Source Code

```cpp
const int ldrPin = A0;
const int ledPin = 7;
int threshold = 500;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int ldrValue = analogRead(ldrPin);
  Serial.println(ldrValue);

  if (ldrValue > threshold) {
    digitalWrite(ledPin, HIGH);
  } 
  else {
    digitalWrite(ledPin, LOW);
  }

  delay(100);
}
```

## How to Run

1. **Connect the Hardware:**  
   - Connect LDR and LED as described.  
   - Connect Arduino to computer using USB.

2. **Open Arduino IDE:**  
   - Paste the code into a new sketch.

3. **Select Board and Port:**  
   - Tools → Board → Arduino Uno  
   - Tools → Port → Select COM port  

4. **Upload Code:**  
   - Click **Upload (→)**  
   - Wait for **Done uploading**

5. **Monitor Output:**  
   - Open **Serial Monitor (9600 baud)**  
   - Change light intensity on LDR (cover/uncover it)

---

## Output

**Behavior:**
- LED turns **ON** when light intensity > threshold (500)  
- LED turns **OFF** when light intensity < threshold  

---

## Explanation of the Code

1. **Pins Setup:**  
   - `ldrPin` reads analog light value  
   - `ledPin` controls LED  

2. **Working Principle:**  
   - LDR changes resistance based on light  
   - Arduino reads value using `analogRead()` (0–1023)

3. **Condition Logic:**  
   - If `ldrValue > 500` → LED ON  
   - Else → LED OFF  

4. **Serial Monitor:**  
   - Displays real-time LDR values  

---

## Viva Questions

1. **What is an LDR?**  
   A sensor whose resistance changes with light intensity.

2. **Which pin is used for LDR?**  
   Analog Pin A0

3. **Why analogRead() is used?**  
   Because LDR gives analog values (0–1023).

4. **What is threshold?**  
   A reference value to compare light intensity.

5. **What happens when light increases?**  
   LED turns ON.

6. **Why use voltage divider?**  
   To convert resistance change into voltage.

7. **Can brightness be controlled instead of ON/OFF?**  
   Yes, using PWM.

---

## Observations

- LED turns ON in bright light.  
- LED turns OFF in low light.  
- Serial monitor shows changing values.

---

## Result

- Successfully controlled LED using LDR sensor.  
- System works correctly based on light intensity.
