# Arduino Serial LED Control Project

## 📝 Description

This project demonstrates serial communication between a computer and an Arduino board to control an LED. Using simple serial commands ('1' and '0'), you can turn an LED on and off through the serial monitor.

## ✨ Features

- Serial communication at 9600 baud rate
- LED control through serial monitor
- Simple command interface ('1' for ON, '0' for OFF)
- Real-time serial feedback

## 🛠️ Hardware Requirements

- Arduino UNO or compatible board
- 1x LED
- 1x 220Ω resistor
- Jumper wires
- USB cable for Arduino

## 📊 Circuit Assembly Steps

1. **LED Preparation**
   - Identify the LED pins:
     * Longer leg is the Anode (+)
     * Shorter leg is the Cathode (-)
   - The LED must be connected with correct polarity to work

2. **Resistor Connection**
   - The 220Ω resistor is essential to protect the LED
   - Color code for 220Ω: Red-Red-Brown-Gold
   - Resistor can be connected to either leg of the LED (we'll use cathode side)

3. **Circuit Connection Steps**
   ```
   Step 1: Arduino Pin 13 → LED Anode (+, longer leg)
   Step 2: LED Cathode (-, shorter leg) → 220Ω Resistor
   Step 3: Other end of 220Ω Resistor → Arduino GND
   ```

## 🔍 Algorithm Explanation

### 1. Initialization Phase
```cpp
void setup() {
    Serial.begin(9600);     // Start serial communication
    pinMode(13, OUTPUT);     // Configure LED pin
}
```
- Serial communication is initialized at 9600 baud rate
- Pin 13 is set as output to control the LED
- This phase runs once when Arduino starts

### 2. Main Control Loop
```cpp
void loop() {
    if(Serial.available() > 0) {    // Check for incoming data
        data = Serial.read();        // Read the data
        Serial.print(data);          // Echo back
        processCommand(data);        // Process the command
    }
}
```

### 3. Command Processing Algorithm
1. **Data Reception**
   - System continuously monitors serial port
   - When data arrives, it's immediately read
   - Only one byte is processed at a time

2. **Command Interpretation**
   - If received byte is '1':
     * LED turns ON
     * Digital pin 13 is set to HIGH
   - If received byte is '0':
     * LED turns OFF
     * Digital pin 13 is set to LOW
   - All other inputs are ignored

3. **Feedback Mechanism**
   - Every received character is echoed back
   - This confirms command reception
   - Helps in debugging and verification

## 🚀 Operating Instructions

1. **Setup Phase**
   - Connect Arduino to computer
   - Upload the provided code
   - Open Serial Monitor
   - Set baud rate to 9600

2. **Control Commands**
   - To turn LED ON:
     * Type: 1
     * Press Send or Enter
   - To turn LED OFF:
     * Type: 0
     * Press Send or Enter

3. **Expected Behavior**
   - Command '1': LED illuminates
   - Command '0': LED turns off
   - Each command is echoed in Serial Monitor

## 🔧 Troubleshooting Guide

1. **LED Not Responding**
   - Verify Circuit:
     * Check LED polarity (long leg to Pin 13)
     * Ensure resistor is properly connected
     * Verify GND connection
   - Code Verification:
     * Confirm code uploaded successfully
     * Check if correct board is selected
     * Verify COM port selection

2. **Serial Communication Issues**
   - Check Settings:
     * Baud rate must be 9600
     * Correct COM port selected
     * Serial Monitor is open
   - Hardware Check:
     * USB cable is properly connected
     * Arduino board is powered
     * Correct drivers are installed

3. **Common Mistakes to Avoid**
   - Reversed LED polarity
   - Missing resistor
   - Wrong baud rate
   - Incorrect pin connections
   - Loose wire connections

## 🔬 Technical Details

1. **Serial Communication**
   - Baud Rate: 9600 bits per second
   - Data Format: 8 bits, no parity, 1 stop bit
   - Flow Control: None

2. **Power Requirements**
   - LED Forward Voltage: ~2V
   - LED Current: ~20mA
   - Resistor Value: 220Ω
   - Operating Voltage: 5V (from Arduino)

3. **Pin Configuration**
   - Digital Pin 13: LED control
   - Built-in LED: Connected to Pin 13
   - GND: Common ground reference

## ✍️ Author

Naila Shehzadi
- GitHub: [NailaShehzadi](https://github.com/Nailashehzadi01)
- Email: Nailashehzadi396@gmail.com




