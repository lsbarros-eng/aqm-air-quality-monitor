# Changelog

All notable changes to AQM will be documented in this file.

## [0.1.0]

### Project identity

- Project renamed to **AQM — Air Quality Monitor** before public release.
- OLED configuration isolated in `display_oled_ssd1306.yaml` using ESPHome packages.
 — 2026-07-23

### Added

- ESP32-based environmental acquisition firmware;
- SCD41 acquisition for CO₂, temperature and relative humidity;
- BME280 acquisition for pressure, temperature and relative humidity;
- SSD1306 OLED local display;
- DS3231-compatible RTC detection;
- local ESPHome web server;
- operational CO₂ and humidity alerts;
- fixed local IP configuration;
- fallback access point and captive portal;
- OTA firmware update support;
- shared I²C bus scan and diagnostic logging.

### Validated

- Hardware Architecture A03, reduced-wiring breadboard prototype;
- I²C addresses `0x3C`, `0x57`, `0x62`, `0x68` and `0x76` detected;
- OTA update completed successfully;
- Wi-Fi operation at fixed IP `192.168.0.240`;
- SCD41 interval changed to 30 seconds to avoid repeated startup timing warnings.

### Known limitations

- No persistent measurement history;
- RTC time not yet synchronized;
- no reference-instrument calibration;
- prototype wiring and enclosure not finalized.
