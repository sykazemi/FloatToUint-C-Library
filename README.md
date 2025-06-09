

# Float32 ↔️ Uint16 Converter for STM32 (C)

> ⚙️ Convert `float` (32-bit IEEE 754) to two `uint16_t` values and back — fast, reliable, and hardware-friendly.  
> 🎯 Designed for embedded systems like STM32 (Little Endian) using C and HAL.

---

## 🚀 Features

- ✅ Convert `float` → `uint16_t[2]` (little-endian order)
- ✅ Convert back `uint16_t[2]` → `float`
- ✅ Uses safe memory union (`typedef union`)
- ✅ No malloc, no dependencies, no surprises
- ✅ Null-pointer safe
- ✅ Clean C-style API, designed for portability

---

## 📦 API Overview

```c
void  FloatToUint16(float value, uint16_t *out);
float Uint16ToFloat(const uint16_t *in);
````

* `out[0]` ← LSB (least significant 16 bits)
* `out[1]` ← MSB (most significant 16 bits)

---

## 🔧 Usage Example

```c
#include "float32_converter.h"
#include <stdio.h>

int main(void) {
    float original = -98.76f;
    uint16_t buffer[2];

    FloatToUint16(original, buffer);
    printf("Float → Uint16s: 0x%04X 0x%04X\n", buffer[0], buffer[1]);

    float recovered = Uint16ToFloat(buffer);
    printf("Recovered float: %f\n", recovered);
}
```

---

## ⚠️ Endianness Notice

This implementation assumes **Little Endian memory layout**, which is standard for STM32 and most ARM Cortex-M devices.
For Big Endian systems, you’ll need to **swap `out[0]` and `out[1]`** when transmitting or storing.

---

## 📁 File Structure

```
float32_converter/
├── float32_converter.h
├── float32_converter.c
└── README.md
```

---

## 📄 License

MIT License — free to use in personal, academic, or commercial projects.
No credit needed, but appreciated 😊

---

## 👤 Author

**Seyed Yasin Kazemi**
Embedded Systems Developer — STM32 | HAL | FreeRTOS | PCB Design

