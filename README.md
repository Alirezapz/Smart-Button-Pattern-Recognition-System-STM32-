# Smart Button Pattern Recognition System (STM32)

## 📌 Overview

This project implements a real-time button press pattern recognition system using an STM32 microcontroller. The system detects different types of button presses (short, long, and medium), evaluates the confidence of each detection, and identifies predefined input patterns. The results are displayed on a 16x2 LCD using a custom low-level driver.

---

## ⚙️ Features

* Real-time button press detection using GPIO
* Classification of press types:

  * Short press
  * Long press
  * Medium (undefined range)
* Confidence calculation based on timing thresholds
* Pattern recognition (e.g., S-S-L, L-S, S-L-S)
* Timeout handling for incomplete sequences
* LCD display interface (4-bit mode, custom driver)

---

## 🧠 How It Works

1. The system continuously monitors a button input (PA0).
2. On each press and release, the duration is measured.
3. The press is classified based on predefined thresholds:

   * SHORT ≤ 300 ms
   * LONG ≥ 800 ms
   * Margin applied for confidence calculation
4. A confidence score is assigned to each press.
5. The sequence is stored and checked against predefined patterns.
6. If a pattern matches:

   * The pattern name is displayed
   * Average confidence is calculated and shown on LCD

---

## 🧾 Recognized Patterns

| Pattern | Description          |
| ------- | -------------------- |
| S-S-L   | Short → Short → Long |
| L-S     | Long → Short         |
| S-L-S   | Short → Long → Short |

---

## 🖥️ Hardware Requirements

* STM32 (e.g., Black Pill / STM32F4 series)
* Push Button (connected to PA0 with pull-up)
* 16x2 LCD (4-bit mode)
* GPIO connections:

  * RS → PB0
  * EN → PB1
  * D4–D7 → PB12–PB15

---

## 🧩 Software Details

* Developed using STM32 HAL library
* Written in C
* Custom LCD driver (no external libraries)
* Timing handled via `HAL_GetTick()`

---

## ⏱️ Key Parameters

```c
#define SHORT_LIMIT   300   // ms
#define LONG_LIMIT    800   // ms
#define RESET_TIMEOUT 2000  // ms
#define MARGIN        0.10f
```

---

## 🚀 Future Improvements

* Add more complex patterns
* Store patterns in EEPROM/Flash
* Interrupt-based button handling
* Add UART debugging interface
* Support multiple buttons

---

## 📷 

<img width="3000" height="4000" alt="20260209_191009" src="https://github.com/user-attachments/assets/30cb4369-d760-4f00-8318-de2250424790" />

---

## 📜 License

This project is provided as-is for educational purposes.
