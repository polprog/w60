# Programming attempts

## TZ32

This is NOT an stm32, or at least NOT pin compatible. Below notes are therefore obsolete.

### Flash

U18 can be read normally (for example with flashrom). The ROM contains several U-boot related strings (but no U-boot itself) and what appears to be images (low entropy chunks)

### MCU

So far MCU is not answering to either JTAG or SWD programming attempts.
This may be related to sharing TDI, TMS and SWDIO with ESP8266's UART pins.

Removing R7 R6 0-ohm links did not allow me to connect with SWD.

The TZ32's BOOT0 pin is floating. TODO: experiment with that. maybe they left the original UART/USB bootloader intact?


## ESP8266EX

### Flash

U3 Flash could not be read while ESP8266 is running.

It's possible to communicate with the ESP8266 using normal tools

```
python3 -m esptool --port /dev/ttyUSB0 --baud 230400 --chip auto chip_id
esptool.py v3.2
Serial port /dev/ttyUSB0
Connecting....
Detecting chip type... Unsupported detection protocol, switching and trying again...
Connecting...
Detecting chip type... ESP8266
Chip is ESP8266EX
Features: WiFi
Crystal is 26MHz
MAC: 4c:11:ae:04:a4:42
Uploading stub...
Running stub...
Stub running...
Changing baud rate to 230400
Changed.
Chip ID: 0x0004a442
Hard resetting via RTS pin...
```

(0 ohm links R7 R6 were removed)