# Troubleshooting

## Device does not appear on the network

1. Check the fallback Wi-Fi access point.
2. Verify `secrets.yaml` values.
3. Confirm that the fixed IP, gateway and subnet match the local network.
4. Use USB logs to inspect Wi-Fi authentication and connection messages.

## `invalid header` boot loop

The flash image is missing or corrupted. Erase and reinstall:

```bash
esptool --chip esp32 --port /dev/ttyUSB0 erase-flash
esphome run firmware/AQM_FW_v0.1.0.yaml --device /dev/ttyUSB0
```

## Serial port cannot be opened

- Close Chrome/ESPHome Web, Arduino IDE and other serial monitors.
- Confirm the device path with `ls /dev/ttyUSB*`.
- Check group membership with `groups`.
- A temporary test is `sudo chmod a+rw /dev/ttyUSB0`.

## Repeated SCD41 `Data not ready`

Use a sensor update interval of 30 seconds. A single warning immediately after boot can be transient; repeated warnings require checking power, wiring and I²C communication.

## BME280 not detected

- Verify VCC and GND directly at the module.
- Check SDA/SCL continuity and possible reversal.
- Scan for both `0x76` and `0x77`.
- Verify that the module is a BME280 rather than a BMP280.

## RTC shows 2000 or 1969

The hardware is detected, but the clock has not yet been synchronized. This is a known v0.1.0 limitation.
