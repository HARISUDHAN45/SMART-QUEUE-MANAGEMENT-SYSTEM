# SMS-Based Token and Queue Management System Using ESP32

## 📌 Project Overview

The **SMS-Based Token and Queue Management System** is an embedded systems project designed to automate token generation and simplify queue management in places such as hospitals, banks, clinics, and service centers.

The system uses an ESP32 microcontroller to generate tokens, a SIM800L GSM module to send token details via SMS, and a 16×2 LCD to display queue information. Users enter their mobile numbers using a keypad to register and receive their token number through SMS.

The operator can call the next user using a NEXT button, restart token numbering using a RESET button, and notify users with a buzzer alert.

## 🎯 Objectives

- Automate token generation and queue management.
- Notify users of their token numbers through SMS.
- Reduce uncertainty and inconvenience associated with physical queues.
- Display the current token and queue status in real time.
- Provide simple operator controls for managing the queue.
- Build a low-cost embedded solution using microcontroller and GSM technology.

## 🛠️ Hardware Requirements

| Component | Purpose |
|---|---|
| ESP32 Development Board | Main controller |
| SIM800L GSM Module | Sends SMS notifications |
| 16×2 I²C LCD | Displays token and queue status |
| 4×3 Keypad | Accepts mobile number input |
| NEXT Push Button | Calls the next token |
| RESET Push Button | Resets the token sequence |
| Buzzer | Provides audible alerts |
| Power Supply | Powers the controller and peripherals |
| Jumper Wires and Breadboard | Circuit connections |

## ⚙️ Working Principle

1. **System Initialization:** The ESP32 initializes the LCD, keypad, GSM module, buttons, and buzzer.
2. **User Registration:** The user enters a mobile number through the keypad.
3. **Token Generation:** The ESP32 assigns a unique token number and stores the associated mobile number in the queue.
4. **SMS Notification:** The SIM800L sends an SMS containing the assigned token number to the registered mobile number.
5. **Queue Display:** The LCD displays the current token and relevant queue information.
6. **Calling the Next User:** When the operator presses NEXT, the ESP32 advances the queue, updates the LCD, and activates the buzzer.
7. **Queue Reset:** When RESET is pressed, the system clears the queue and restarts token numbering from 1.

## 🔌 Hardware Connections

### ESP32 Pin Configuration

| Component | ESP32 Pin | Function |
|---|---|---|
| LCD SDA | GPIO 21 | I²C data |
| LCD SCL | GPIO 22 | I²C clock |
| SIM800L TXD | GPIO 16 (RX2) | GSM serial input to ESP32 |
| SIM800L RXD | GPIO 17 (TX2) | ESP32 serial output to GSM |
| Keypad Row 1 | GPIO 32 | Keypad input/output |
| Keypad Row 2 | GPIO 33 | Keypad input/output |
| Keypad Row 3 | GPIO 25 | Keypad input/output |
| Keypad Row 4 | GPIO 26 | Keypad input/output |
| Keypad Column 1 | GPIO 27 | Keypad input/output |
| Keypad Column 2 | GPIO 14 | Keypad input/output |
| Keypad Column 3 | GPIO 12 | Keypad input/output |
| NEXT Button | As configured in firmware | Next-token control |
| RESET Button | As configured in firmware | Queue reset |
| Buzzer | As configured in firmware | Audible notification |

**Note:** The NEXT, RESET, and buzzer pins depend on the final circuit and firmware configuration. Update this table to match the actual wiring before publishing.

### Important Power Considerations

- Power the SIM800L using a suitable supply within its specified voltage range, typically around 3.4–4.4 V.
- The SIM800L can draw current peaks approaching 2 A during GSM transmission. Use a supply capable of handling these peaks.
- Connect the ESP32 and SIM800L grounds together.
- Ensure UART voltage compatibility; do not connect an ESP32 GPIO directly to a signal that exceeds its permitted input voltage.
- Use a SIM card with SMS service and ensure adequate GSM network coverage.
- Do not power the SIM800L directly from the ESP32 3.3 V output.

## 💻 Software Requirements

- Arduino IDE
- ESP32 board support package
- Keypad library
- LiquidCrystal_I2C library
- Serial communication support for the SIM800L

Install the ESP32 board package and required libraries through the Arduino IDE before compiling the firmware.

## 🚀 Installation and Setup

1. Clone or download this repository.
2. Open the project source file in Arduino IDE.
3. Install the required libraries.
4. Select the appropriate ESP32 board and COM port.
5. Connect the LCD, keypad, GSM module, buttons, and buzzer according to the circuit configuration.
6. Insert an active SIM card into the SIM800L module.
7. Verify the GSM module's power supply and network registration.
8. Upload the firmware to the ESP32.
9. Open the Serial Monitor to inspect initialization messages and troubleshoot communication issues.
10. Enter a mobile number and verify that the token SMS is received.
11. Test the NEXT and RESET buttons and confirm the LCD and buzzer behave as expected.

## 📱 Example SMS Notification

```text
Queue Token System

Your token number is: 05

Please wait until your token is called.
```

*The actual message format depends on the firmware implementation.*

## 🖥️ Example LCD Display

```text
Token System
Now Serving: 03
```

After the NEXT button is pressed, the displayed serving token advances to the next eligible user.

*The exact LCD layout depends on the implemented display logic.*

## ✨ Key Features

- Automatic token number generation
- SMS-based token confirmation
- Keypad-based mobile number registration
- Real-time LCD status display
- Operator-controlled queue advancement
- Buzzer-based alerts
- Queue reset functionality
- Low-cost embedded hardware implementation

## 🏥 Applications

- Hospitals and clinics
- Banks and financial service counters
- Government service centers
- Customer support centers
- Laboratories and diagnostic centers
- Small businesses with customer queues

## 🔮 Future Improvements

- Send an SMS when a user's turn is approaching.
- Add estimated waiting-time calculation.
- Store queue information in non-volatile memory.
- Add duplicate mobile-number validation.
- Implement protection against accidental queue resets.
- Add a web dashboard for remote queue monitoring.
- Introduce multiple service counters and priority queues.

## ⚠️ Limitations

- SMS delivery depends on GSM network availability and the SIM card's service status.
- The SIM800L requires a compatible 2G GSM network, which may not be available in every region.
- Queue data may be lost after a power failure unless persistent storage is implemented.
- The RESET operation may erase active queue information if confirmation and recovery mechanisms are not implemented.

## 📚 Technologies Used

- Embedded C/C++  
- ESP32 Microcontroller  
- GSM Communication (SIM800L)  
- UART Serial Communication  
- I²C Communication  
- LCD Interfacing  
- Keypad Interfacing  
- Digital Input/Output Control  

## 👨‍💻 Project Status

Developed as an embedded systems project demonstrating microcontroller programming, GSM-based SMS communication, peripheral interfacing, and automated queue management.

## 📄 License

This project is available for educational and learning purposes. Add a specific open-source license if you intend to permit reuse, modification, and redistribution under defined terms.
