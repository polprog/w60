# Programming attempts

## TZ32

### Flash

U18 can be read normally (for example with flashrom). The ROM contains several U-boot related strings (but no U-boot itself) and what appears to be images (low entropy chunks)

### MCU

So far MCU is not answering to either JTAG or SWD programming attempts.
This may be related to sharing TDI, TMS and SWDIO with ESP8266's UART pins.


## ESP8266EX

### Flash

U3 Flash could not be read while ESP8266 is running. 