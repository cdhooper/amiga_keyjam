# KeyJAM Firmware

KeyJAM runs firmware on an STM32F205 microcontroller. The firmware
implements a dual-port USB host stack with USB hub support, translates
USB HID keyboard, mouse, and gamepad input into Amiga keyboard and
mouse / joystick signals, and sends mouse scroll wheel movement to the
Amiga as keystrokes, so no wheel driver is needed on the Amiga.

## Current status

- Keyboard and one mouse/joystick port are supported.
- Support for both mouse/joystick ports (P0 and P1) is planned.
- USB hub hotplug handling needs improvement; see the
  [Supported USB Devices](usb_supported_devices.txt) list for details.

## Updating firmware over USB-C

KeyJAM firmware is updated through the STM32 built-in USB DFU bootloader,
using the USB-C port.

1. Install both **Type-C Data** jumpers (see [Installation](installation.md#jumpers)).
2. Connect the KeyJAM USB-C port to your computer.
3. Press and hold **STM DFU**, press and release **STM RESET**, then release **STM DFU**.
   KeyJAM is now in DFU mode.
4. Program the firmware using `dfu-util` or STM32CubeProgrammer. For example:

   ```
   dfu-util -a 0 -s 0x08000000:leave -D keyjam.bin
   ```

5. Press **STM RESET** (or power cycle) if KeyJAM did not restart on its own.

## Serial console

A 3-pin console header (GND, Tx, Rx) on the left edge of the board
provides a 3.3V serial console for diagnostic output and commands. Use a
3.3V USB-to-serial adapter; do not connect RS-232 level signals.

## SWD

The 6-pin STM32 SWD header (V3P3, CLK, GND, DAT, NRST, TDO) can be used
with an ST-LINK or other SWD probe for programming and debugging.

## Key remapping with becky

**becky** is a graphical AmigaOS tool, originally written for AmigaPCI,
which lets you remap USB keyboard keys and mouse / gamepad buttons to
Amiga keys and buttons. becky also works with KeyJAM, allowing the same
remapping.

## USER button

The **USER** button is read by the firmware. Its function depends on the
firmware version.
