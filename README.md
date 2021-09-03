# DREVO Calibur V2 TE Reverse Engineering
This is partial and may or may not be completed. Use this information at your own discretion and risk.

## Specification

- 71-key (Layout with ANSI 60% plus arrow clusters and nav clusters)
- RGB Front/Side lights
- USB-C (Wired)

## MCU

This keyboard uses the HFD2201KBA in a LQFP64 package.
Appears to be based on/clone of SONiX SN32F248B.

[https://www.eevblog.com/forum/microcontrollers/hfd2201kba-any-details-on-this-microcontroller/](https://www.eevblog.com/forum/microcontrollers/hfd2201kba-any-details-on-this-microcontroller/)  
[https|:/|www.sonix.com.tw/list-en-4336](https://www.sonix.com.tw/list-en-4336)  
[https://www.sonix.com.tw/article-en-4336-30356](https://www.sonix.com.tw/article-en-4336-30356)  

## Key Matrix

|Rows|Pin#|GPIO Name|
|:-|:-|:-|
|0|63|D11 (P3.11 in SN32F248B datasheet)|
|1|62|D10|
|2|61|D9|
|3|60|D8|
|4|59|D7|

|Columns|Pin#|GPIO Name|
|:-|:-|:-|
|0|25|A8 (P0.8 in SN32F248B datasheet)|
|1|26|A9|
|2|27|A10|
|3|28|A11|
|4|29|A12|
|5|30|A13|
|6|31|A14|
|7|32|A15|
|8|34|B0 (P1.0 in SN32F248B datasheet)|
|9|35|B1|
|10|36|B2|
|11|37|B3|
|12|38|B4|
|13|39|B5|
|14|40|B6|
|15|41|B7|

## LED Matrix

### Key backlight

|Rows|GPIO Name(RGB output)|
|:-|:-|
|0|C4, C5, C6|
|1|C7, C8, C9|
|2|C10, C11, C12|
|3|C13, C14, B13|
|4|D3, B15, B14|

|Columns|GPIO Name|
|:-|:-|
|0|A8|
|1|A9|
|2|A10|
|3|A11|
|4|A12|
|5|A13|
|6|A14|
|7|A15|
|8|B0|
|9|B1|
|10|B2|
|11|B3|
|12|B4|
|13|B5|
|14|B6|
|15|B7|

### Side light

RGB LEDs on both sides of the case.  

|Rows|GPIO Name(RGB output)|
|:-|:-|
|0|D4, D5, D6|

|Columns|GPIO Name|
|:-|:-|
|0|C1|
|1|C0|
|2|B12|
|3|B11|
|4|B10|
|5|B9|

## Pin Access

![img](/img/pcb01.jpg)  

### BOOT pin

Bootloader mode:  
Short BOOT pin and GND pin after that connect to your PC.  
To write to Bootloader mode, specify VID:0C45 PID:7040.  

### SWD pin

Unconfirmed.

## SONiX QMK

This keyboard source code was based on Redragon K530 keyboard.
[https://github.com/SonixQMK/qmk_firmware/tree/sn32/keyboards/drevo/caliburv2te71/](https://github.com/SonixQMK/qmk_firmware/tree/sn32/keyboards/drevo/caliburv2te71/)  

## Flash

Flashing software for windows: [SONiX_USB_MCU_ISP_Tool_V2.3.1.7-.zip](https://github.com/qmk/qmk_firmware/files/5862715/SONiX_USB_MCU_ISP_Tool_V2.3.1.7-.zip)  

When loading the file, select SN32F24xB, then select your built hex/bin file.

