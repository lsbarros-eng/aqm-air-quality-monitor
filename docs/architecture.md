# Architecture A03

## System definition

AQM v0.1.0 uses an ESP32-32D as the acquisition, processing and communication unit. Environmental sensors and the OLED share a single I²C bus.

```text
5 V USB supply
      │
      ▼
ESP32 expansion board
      │
      ├── ESP32-32D
      │     ├── Wi-Fi web server
      │     ├── OTA update service
      │     └── operational alert logic
      │
      └── I²C bus: SDA GPIO21 / SCL GPIO22
            ├── SSD1306 OLED      0x3C
            ├── SCD41             0x62
            ├── RTC               0x68
            ├── BME280            0x76
            └── RTC EEPROM        0x57, when present
```

## Architectural decisions

- **ESPHome** was selected to accelerate sensor integration, web visualization and OTA development.
- **I²C** allows the current sensors and display to share two data pins.
- **SCD41** is the primary CO₂ sensor and also provides temperature and humidity.
- **BME280** adds atmospheric pressure and a second temperature/humidity channel for comparison.
- **Fixed local IP** provides predictable access to the embedded web page.
- **OTA** reduces the need for repeated physical USB access after the initial installation.

## Version identification

- System: AQM v0.1.0
- Firmware: v0.1.0
- Hardware: Architecture A03
- Stage: Reduced-wiring breadboard prototype

## Display modularity

The display subsystem is separated from the acquisition firmware. The main file loads
`firmware/display_oled_ssd1306.yaml` as an ESPHome package. The package owns fonts,
display driver settings and rendering logic, while sensor IDs remain defined in the
main firmware.

This boundary allows a future SPI TFT implementation to be developed as a replacement
package without changing the I²C sensor definitions, Wi-Fi configuration or alerts.
