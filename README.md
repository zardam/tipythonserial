# TI-83 Python module as USB to serial bridre

This is some ugly code to transform a TI-Python adapter into an USB to serial bridge, which is working with the calculator.

The USB to serial bridge is written in the space used by the FAT file system of the embedded CircuitPython. So, the original firmware code is still present and is used to bypass the verification made by the calculator. As the start address of the firmware is not the standard one, a specific boot loader is needed.

## Warning !

Do not try this if you do not have a way to recover the module (SWD adapter or something similar).

## Building

Just run the `build` script. An ARM compiler and nodejs (at least) are required.

## Installing

1. Connect the module to the computer
2. Put the module in bootloader mode by pressing reset two times quickly
3. Flash the new bootloader by copying bin/update-bootloader.uf2 to the virtual drive. The module will reboot into the bootloader.
4. Flash the USB to serial firmware by copying bin/usb_serial.uf2 to the virtual drive.
5. On the first connection to the calculator, the firmware will be upgraded. This is normal and will be done only once.

## Using it

On the back of the module board, TP5 is UART RX, TP6 is UART TX. The UART parameters (hardcoded) are 115200 8N1.

## Acknowledgments

Thanks to [tinyusb](https://github.com/hathach/tinyusb) and [uf2-samdx1](https://github.com/microsoft/uf2-samdx1) !
