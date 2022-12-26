# PCIce
A PCI Express card with an inbuilt PWM fan controller and mounting points for an 80mm fan.
## Hardware
The hardware is based on an ATtiny13A which outputs a 25kHz PWM signal to the fan. A button is used for speed control, and the current speed is displayed on four multiplexed LEDs.
## Firmware
### Functionality
The firmware attempts to load the speed setting from EEPROM on boot. The speed setting is stored twice to guard against corruption. The second copy is inverted to detect a blank EEPROM. The speed will default to maximum if corruption is detected to prevent overheating. The button is debounced in software and must be released for a short period before the next press is registered.
### Building
The firmware can be compiled and flashed with the `build` script inside the firmware directory. This script expects an AVRISP MKII to be connected over USB. `avr-gcc`, `avr-objcopy`, `avrdude` and `avr-libc` are required to build the firmware.