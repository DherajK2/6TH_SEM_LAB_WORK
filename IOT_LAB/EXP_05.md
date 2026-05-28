## Aim

To connect the Arduino board to an available **Wi‑Fi network** and display the assigned **IP address** on the Serial Monitor using the `WiFiS3` library.[^2][^1]

## Materials Required

- Arduino Uno R4 WiFi
- USB cable
- Computer with Arduino IDE
- Available Wi‑Fi network
- Wi‑Fi SSID and password[^2]


## Construction

This experiment does not require an external circuit because the Wi‑Fi module is built into the **Arduino Uno R4 WiFi** board. The board is connected directly to the computer using a USB cable, and the Wi‑Fi credentials are provided in the program.[^2]

## Source Code

```cpp
#include <WiFiS3.h>

// Wi-Fi credentials
const char* ssid = "Dheraj";        // Replace with actual WiFi name
const char* password = "123456dk0"; // Replace with actual WiFi password

void setup() {
  Serial.begin(115200);

  unsigned long startMillis = millis();
  while (!Serial && millis() - startMillis < 5000);

  Serial.println("Serial is working!");
  Serial.print("Connecting to WiFi: ");
  Serial.println(ssid);

  WiFi.begin(ssid, password);

  int maxAttempts = 30;
  while (WiFi.status() != WL_CONNECTED && maxAttempts > 0) {
    Serial.print(".");
    delay(500);
    maxAttempts--;
  }

  if (WiFi.status() == WL_CONNECTED) {
    Serial.println("\nConnected to WiFi!");
    Serial.print("IP Address: ");
    Serial.println(WiFi.localIP());
  } else {
    Serial.println("\nFailed to connect to WiFi. Check SSID/Password or Router.");
  }
}

void loop() {
  if (WiFi.status() == WL_CONNECTED) {
    Serial.print("Connected. IP Address: ");
    Serial.println(WiFi.localIP());
  } else {
    Serial.println("Not connected to WiFi.");
  }
  delay(5000);
}
```

The function `WiFi.localIP()` returns the local IP address assigned to the board after it joins the network.[^1]

## How to Run

1. Connect the Arduino Uno R4 WiFi board to the computer using a USB cable.[^2]
2. Open Arduino IDE and paste the program into a new sketch.
3. Select the correct board and port from the **Tools** menu.
4. Replace the `ssid` and `password` values with the actual Wi‑Fi name and password.
5. Upload the code and open the **Serial Monitor**.
6. Set the baud rate to **115200** and observe the connection status and IP address.[^2]

## Output

**Serial Monitor Example:**

```text
Serial is working!
Connecting to WiFi: Dheraj
........
Connected to WiFi!
IP Address: 192.168.1.8
```

**Repeated Output in loop():**

```text
Connected. IP Address: 192.168.1.8
Connected. IP Address: 192.168.1.8
```

The board prints its assigned local IP address once connected, and it can continue reporting the IP periodically through the Serial Monitor.[^1][^2]

## Explanation of the Code

1. **Library Inclusion:**
`#include <WiFiS3.h>` includes the Wi‑Fi library used by Arduino UNO R4 WiFi boards.[^2]
2. **Wi‑Fi Credentials:**
The `ssid` and `password` variables store the network name and password required to connect to the router.[^2]
3. **Serial Communication:**
`Serial.begin(115200);` starts serial communication so the connection messages and IP address can be viewed in the Serial Monitor.
4. **Connecting to Wi‑Fi:**
`WiFi.begin(ssid, password);` starts the connection process to the specified Wi‑Fi network.[^2]
5. **Checking Connection Status:**
`WiFi.status()` is used to check whether the board is connected to the network.
6. **Displaying IP Address:**
After successful connection, `WiFi.localIP()` displays the local IP address assigned by the router.[^1][^2]

## Viva Questions

1. **Which library is used for Wi‑Fi connection in this experiment?**
`WiFiS3.h` is used for Wi‑Fi connectivity on UNO R4 WiFi.[^2]
2. **What is the function of `WiFi.begin(ssid, password)`?**
It starts connecting the board to the given Wi‑Fi network.[^2]
3. **What does `WiFi.localIP()` do?**
It returns the local IP address assigned to the Arduino board.[^1]
4. **Why is Serial Monitor used here?**
It displays the connection status and the IP address.
5. **What happens if the SSID or password is wrong?**
The board fails to connect and shows a failure message.
6. **Does this experiment need external components like LEDs or sensors?**
No, because the Wi‑Fi module is built into the board.[^2]
7. **Which Arduino board is suitable for this program?**
Arduino Uno R4 WiFi, because it supports the built‑in `WiFiS3` library.[^2]

## Observations

- The Arduino attempts to connect to the specified Wi‑Fi network after startup.
- Once connected, the Serial Monitor shows the assigned IP address.
- If the connection fails, an error message is displayed instead of the IP address.[^1][^2]


## Result

- Successfully connected the Arduino board to the available Wi‑Fi network.
- Displayed the assigned IP address on the Serial Monitor using `WiFi.localIP()`.[^1][^2]

If you want, I can also format this into the exact same polished lab-record style as your previous experiment, with headings, spacing, and wording matched line by line.
<span style="display:none">[^10][^3][^4][^5][^6][^7][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://energia.nu/guide/libraries/wifi/wifi_localip/

[^2]: https://docs.sunfounder.com/projects/elite-explorer-kit/en/latest/new_feature_projects/01_1_connect_to_wifi.html

[^3]: https://github.com/espressif/arduino-esp32/issues/10580

[^4]: https://www.facebook.com/groups/ArduinoPH/posts/4201473953429732/

[^5]: https://www.reddit.com/r/Cplusplus/comments/1cyoip1/librarie_wifis3_udp_transmit_integer_uno_r4_wifi/

[^6]: https://forum.arduino.cc/t/arduino-wifi-config-not-working/1117663

[^7]: https://forum.arduino.cc/t/how-to-disconnect-and-reconnect-wifi-using-wifis3-on-arduino-uno-r4-wifi/1390216

[^8]: https://www.arduinolibraries.info/libraries/r4-http-client

[^9]: https://docs.espressif.com/projects/arduino-esp32/en/latest/api/wifi.html

[^10]: https://docs.particle.io/reference/device-os/api/wifi/localip/

