# STM32-with-Arduino-Host-Shield
This project is used to connect Android device with STM32 using Android ADK(2011).  
The demokit of orignal ADK use Arduino ADK or Arduino with USB Host Shield.  The object is 
porting Arduino USB host shield to STM32 using STM32F070 Nucleo.  

## Power Consideration
USB host shield need to provide power to device.  We need to configure the Nucleo board using external power.

* JP1 off (Disconnect USB power from PC)
* JP5 connect 2,3 pin, using E5V.  

We will provide 7-12V from the VIN pin of Arduino Connector(CN6 pin 8)

## Interface pins

Using STM32 CubeMX configure the Arduino pinout for USB Host Shield.  

| CPU Pin          | Arduino PIN   | CN5 pin|
| ---------------  |:-------------:| ------:|
| SPI1_SCK (PA5) * | D13           |   6   |
| SPI1_MISO(PA6)  | D12           |   5   |
| SPI1_MOSI(PA7)  | D11           |   4   |
| MAX3421E_SS(PB6)| D10           |   3   |
| MAX3421E_INT(PC7)| D9           |   2   |
| MAX3421E_GPX(PA9)| D8           |   1   |

**PA5** was used as LED in Nucleo board.  Since SPI1_SCK is output, it should be OK just leave the LED connected.  If not, 
disconnect the SB21 at the back of board.

## Power Pins
| Power Pins  | Arduino Pin | CN6 Pin|
| ----------  | ----------- | ------ |
| VIN (7-12V) | VIN         |  8     |
| GND         | GND         |  6-7   |


## Arduino ADK Library
Download orginal Android ADK library from [this link.] (https://android-review.googlesource.com/admin/repos/device/google/accessory/arduino)


