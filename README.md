# Precompiled Micropython ESPNow Images for the ESP32 and ESP8266
A collection of pre-compiled micropython images (including espnow support) for the esp32 and esp8266.

These are provided as a convenience for users until the ESPNow code is accepted into a Micropython release.

These images are compiled from the **espnow-g20*** branches at https://github.com/glenn20/micropython.

The Pull Request for ESPNow support is available at: https://github.com/micropython/micropython/pull/6515.

Each folder contains the following firmware images:
- `firmware-esp32-GENERIC.bin`: For the ESP32 GENERIC build target.
- `firmware-esp8266-GENERIC_1M.bin`: For the ESP8266 GENERIC_1M build target (1MB RAM devices)
- `firmware-esp8266-GENERIC.bin`: For the ESP8266 GENERIC build target (2+MB RAM devices)

Firmware images are provided in the following folders:
- `20210128_espnow-g20_gba813d8f9`:
  - Branch **espnow-g20** (commit ba813d8f9) espnow patches applied against Micropython **master** on 28 Jan 2021.
- `20210128_espnow-g20-v113_gb560287eb`:
  - Branch **espnow-g20-v113** (commit b560287eb) espnow patches applied against Micropython release **v1.13** on 28 Jan 2021.

These images are built following the instructions at https://github.com/micropython/micropython/blob/master/ports/esp32/README.md and https://github.com/micropython/micropython/blob/master/ports/esp8266/README.md.

Images can be written to the ESP32 and ESP8266 devices over usb using esptool.py (install using pip), eg:

```
esptool.py --port /dev/ttyUSB0 --baud 115200 write_flash --flash_size=4MB --flash_mode=qio 0 firmware-esp8266-GENERIC_1M.bin
```

or

```
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x1000 firmware-esp32-GENERIC.bin
```
