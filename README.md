# HD-W60 reverse engineering


HD-W60 is a small, affordable LED controller board available from various online outlets. This repository aims to document, reverse engineer, and provide development tools the board, as it is a feature rich Wi-Fi enabled device. 


![Image of a HD-W60 v1.5 PCB](board.jpg)


# Hardware

HD-W60 v1.5 hardware contains the following MCUs and peripherals:

- TZ32F202C3T6 (For now I assume it is an STM32F202C3T6 clone)
- ESP8266EX (A well known WiFi enabled SoC)
- AiP8563 I²C RTC with backup battery
- 74HC245 output drivers



The board has several IO ports listed below in no particular order:

- LED panel connections (2x HUB12 and 1x HUB8)
- USB host port
- Several GPIOs broken out on various headers
- ESP8266 USART (P20 header)

I believe that it can be turned into a powerful IoT development board if it is possible to run custom code on it.

# Peripheral structure

- U4 TZ32F202C3T6
  - U5 AiP8563
  - U18 P25Q16H
  - U6, U31 74HC245
- U1 ESP8266EX
  - U3 P25Q16H


# STM32 peripherals

The STM32 drives two output drivers for the LED panels with U31 and U6 74HC245. The USB port is connected to this MCU. STM32 is also connected to the U18 P25Q16H serial flash. 

## Headers 

### P12 (power)

| Pin | Function |
|-----|----------
| 1   | Vdd |
| 2   | Vss |
| 3   | GND |

### ISP (U18 serial flash programming header)

| Pin | Function |
|-----|----------
| 1   | CS# |
| 2   | SI  |

SO is not connected, readot must be done via a SOIC clip.

### P5

| Pin | Function |
|-----|----------
| 1   | +5V |
| 2   | PB3 |
| 3   | GND |

### P11

| Pin | Function |
|-----|----------
| 1   | +5V |
| 2   | PB4 |
| 3   | GND |

### Sx headers

Pin 2 is ground on all 3. All 3 pins pulled up to 3v3

| Header | Pin 1 function |
|-----|----------
| S2   | PF0  |
| S3   | PC15 |
| S4   | PA0  |


# ESP8266 peripherals

Only U2 serial flash is connected to the ESP8266

## Headers

### P20

| Pin | Function |
|-----|----------
| 1   | U0TXD |
| 2   | U0RXD |

### Sx headers

Pin 2 is ground on all 3. All 3 pins pulled up to 3v3

| Header | Pin 1 function |
|------|----------
| S5   | GPIO0  |
| S6   | GPIO4  |


# Licence


[CC0](http://creativecommons.org/publicdomain/zero/1.0/") - to the extent possible under law, the person who associated CC0 with this 
work has waived all copyright and related or neighboring rights to this work.
