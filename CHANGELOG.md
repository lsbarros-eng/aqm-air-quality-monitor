# Changelog

All notable changes to AQM will be documented in this file.

## [0.1.2] — 2026-07-31

### Added

- RTC synchronization using SNTP;
- DS3231 time read during system startup;
- automatic writing of synchronized network time to the physical RTC.

### Changed

- SCD41 configured explicitly in periodic measurement mode;
- SCD41 measurement interval changed to 60 seconds;
- SCD41 temperature offset configured to 4.0 °C;
- SCD41 automatic self-calibration enabled.

### Validated

- ESPHome configuration validation completed successfully;
- OTA firmware installation completed successfully;
- correct date and time retained after power interruption and restart.

## [0.1.1] — 2026-07-27

### Changed

- Firmware file renamed from `AQM_FW_v0.1.0.yaml` to `AQM_FW_v0.1.1.yaml`;
- internal system and firmware version identifiers updated to v0.1.1;
- release focus documented in the firmware header.

### Added

- ESPHome build artifacts and local secrets excluded through `firmware/.gitignore`.


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
