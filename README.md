# Ultrasonic Sensor Script.
## Disclaimer: I have not tested it on a chip other than the LILYGO TTGO T8. It should work on boards without a display too, but I do not guarantee it.
You will need the espressif IDF in order to compile the script from source or esptool to flash the precompiled .bin files:

- [ESP32 Getting Started Guide](https://docs.espressif.com/projects/esp-idf/en/stable/get-started/index.html)
- [ESP32-S2 Getting Started Guide](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/get-started/index.html)
- install esptool: `pip install esptool`

### Compile instructions from source:
- navigate to source folder (this one)
- get the idf tool: `source <your-idf-installation>/export.sh`
- set your board: for ESP32: `idf.py set-target esp32` | for ESP32S2: `idf.py set-target esp32s2`
- compile: `idf.py build`
- flash to chip: `idf.py -p <port> flash monitor`, but `monitor` is optional when you ude the T8 display

### Flash precompiled:
##### These binaries can ONLY be flashed on esp32s2 chips with a flash size of 4MB:
- download the 3 .bin files (`bootloader.bin`, `partition-table.bin` and `ultrasonic.bin`)
- go to that directory
- flash to chip: `esptool.py --chip esp32s2 --port <port> write_flash 0x1000 bootloader.bin 0x8000 partition-table.bin 0x10000`

### Connection instructions:
- the display is integrated into the development board
- Trigger Pin: GPIO4
- Echo Pin: GPIO5
