# 📡 PLC_and_HTTP_Scanner

A hybrid embedded system that collects real-time data from an industrial ControlLogix PLC and remote HTTP APIs, encodes the combined data into a binary NDEF message, and stores it on an ST25DV NFC chip. When a phone scans the NFC tag using a React Native app, it decodes and displays structured operational metrics, fault counts, system states, and sensor values.

---

## 💡 Features

- **📊 PLC Snapshot Encoding**  
  Captures word-level and bit-level status data from a ControlLogix PLC.

- **🌐 HTTP Float Integration**  
  Pulls external float metrics (e.g., speeds, temperatures, fault rates) via HTTP.

- **📦 Binary Packing**  
  Efficiently serializes snapshot + float data into a compact NDEF message.

- **📶 Chunked I2C Writes**  
  Automatically splits large payloads into 256-byte I2C chunks for NFC memory compatibility.

- **📱 React Native Frontend**  
  Reads and parses the NFC data on Android/iOS using `react-native-nfc-manager`.

- **🔁 Endian-Aware Decoding**  
  Interprets 2-byte words and 4-byte floats with correct byte order.

---

## 🧱 Stack

- **Microcontroller:** STM32H7 (STM32CubeIDE, C)
- **NFC Chip:** ST25DV64KC (I2C)
- **PLC:** ControlLogix (EtherNet/IP)
- **HTTP Client:** Mongoose (on STM32)
- **Frontend App:** React Native (TypeScript)

---

## 🚀 Use Case

Ideal for machine builders, commissioning engineers, or plant technicians who need to access real-time system data without plugging in. Just tap your phone to the machine — no app login or network required.

---

## Optimizations

- Payloads over 256 bytes are automatically chunked to conform with ST25DV NFC memory constraints.
- All decoding routines are endian-safe to ensure cross-platform compatibility.
- HTTP float values are compacted before writing to minimize space.

---
