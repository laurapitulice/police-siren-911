
# 🚨 ESP32 "Police Siren" 
Year 1 team project: Bluetooth-controlled Police Siren in Arduino IDE (C++), with hardware implementation using ESP32. It features two different patterns controlled from an Android phone via Bluetooth, integrating flashing LEDs and adjustable buzzer frequencies.

## Components Used
* **Microcontroller:** ESP-32
* **Sound:** 1x Buzzer
* **Visuals:** 1x Blue LED, 1x Red LED 
* **Circuitry:**
    * Breadboard 
    * 2x Resistors (to protect the LEDs)
    * Male-to-Male jumper wires
* **Control Device:** A laptop, PC, or Android phone to upload code and send commands


##  Circuit Setup
The assembly is built on a breadboard with the following configurations:
* **LEDs:** Connected to **Pin 18** and **Pin 22**. They are wired in series with resistors; the anodes (+) connect to the pins, and the cathodes (-) connect to Ground (GND).
* **Buzzer:** The positive terminal is connected to **Pin 16**, and the negative terminal is connected to Ground (GND).
* **Connection:** The ESP32 is linked to the laptop via a USB-A to MicroUSB cable for programming in **Arduino IDE 2.3.2**.


## Functionality & Features
The project utilizes the `BluetoothSerial` library to receive commands from the "Serial Bluetooth Terminal" mobile app. It manages three distinct states using an `enum SirenState`:

### Siren Patterns
1.  **Pattern 1 (Wail):** Gradually increases frequency from 600Hz to 1200Hz and back. LEDs flash alternately during the transition.
2.  **Pattern 2 (Yelp):** Alternates quickly between 800Hz and 1000Hz tones. This is accompanied by rapid LED blinking
3.  **Stopped:** Silences the buzzer and turns off all LEDs.

### Bluetooth Control
You can switch between patterns by sending the following characters via Bluetooth (Device name: **"esp911"**):
* `1` → Activates **Pattern 1** 
* `2` → Activates **Pattern 2** 
* `0` → **Stops** the siren 



## Code Structure
The software is organized into specific functions for modularity:
* `setup()`: Configures pin modes, initializes Serial communication at 115200 baud, and sets up PWM for the buzzer on Channel 0.
* `Pattern1()` & `Pattern2()`: Contain the logic for sound frequencies and LED timing.
* `loop()`: Continuously checks for Bluetooth data and updates the `currentState`.


