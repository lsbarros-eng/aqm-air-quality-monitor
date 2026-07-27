# Commissioning procedure

## 1. Visual and electrical inspection

- Verify the module pin labels rather than relying only on wire colours.
- Check continuity from the ESP32 expansion board to each module.
- Check that 3V3 and GND are not shorted.
- Power the system from one source only.

## 2. Initial USB installation

```bash
esphome run firmware/AQM_FW_v0.1.0.yaml --device /dev/ttyUSB0
```

If Linux reports a serial-permission error, add the user to `dialout` and log in again:

```bash
sudo usermod -aG dialout "$USER"
```

## 3. Startup checks

Confirm in the logs:

- successful boot;
- I²C bus recovery and scan;
- SCD41 serial number;
- BME280 recognition;
- Wi-Fi connection;
- expected fixed IP;
- OTA service enabled.

## 4. Functional checks

- OLED shows CO₂, temperature, humidity, pressure and RTC field;
- web page opens from another device on the same network;
- sensor values update;
- no persistent `Data not ready` warnings after startup;
- no ESP32 resets or Wi-Fi dropouts during at least one hour.

## 5. Acceptance record for v0.1.0

- Fixed IP: `192.168.0.240`
- Web server port: `80`
- OTA port: `3232`
- SCD41 update interval: `30 s`
- BME280 update interval: `30 s`
- OLED update interval: `5 s`
