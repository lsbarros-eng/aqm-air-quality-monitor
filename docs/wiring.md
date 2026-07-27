# Wiring

## Shared I²C bus

Connect all I²C devices in parallel.

| ESP32 | SCD41 | BME280 | SSD1306 | RTC |
|---|---|---|---|---|
| 3V3 | VIN/VCC* | VCC | VCC | VCC* |
| GND | GND | GND | GND | GND |
| GPIO21 | SDA | SDA | SDA | SDA |
| GPIO22 | SCL | SCL | SCL | SCL |

\* Verify the actual breakout-board supply requirements before connecting. Logic levels must remain compatible with the ESP32's 3.3 V GPIOs.

## Practical recommendations

- Keep SDA and SCL reasonably short.
- Use a consistent wire-colour convention.
- Keep environmental sensors away from the ESP32 regulator, display backplane and other heat sources.
- Do not power the ESP32 simultaneously through multiple USB/VIN inputs unless the board documentation explicitly supports it.
- Verify continuity and absence of a short between 3V3 and GND before power-up.

## Expected scan

A successful startup should normally detect:

```text
0x3C — SSD1306
0x57 — EEPROM on some RTC modules
0x62 — SCD41
0x68 — RTC
0x76 — BME280
```
