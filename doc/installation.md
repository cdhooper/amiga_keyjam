# KeyJAM Installation

This document covers connecting KeyJAM to your Amiga, choosing cables,
powering KeyJAM, and setting jumpers.

[![](2026_05_23_keyjam_rev1_with_cables_attached.jpg)](2026_05_23_keyjam_rev1_with_cables_attached.jpg)

## Cables

[![](2026_05_23_keyjam_cables.jpg)](2026_05_23_keyjam_cables.jpg)

| Cable | Board end | Amiga end | Use |
| ----- | --------- | --------- | --- |
| Mouse / joystick | 2x5 header (P0 or P1) | DB9 female | Amiga mouse port or joystick port |
| Keyboard (DIN) | Keyboard header | 5-pin DIN male | A2000, A3000 keyboard port |
| Keyboard (A4000) | Keyboard header | 6-pin mini-DIN male | A4000 keyboard port |

[![](2026_05_23_keyjam_a4000_keyboard_cable.jpg)](2026_05_23_keyjam_a4000_keyboard_cable.jpg)

Rev 1 boards also have an on-board 5-pin DIN keyboard socket. It is
wired in parallel with the keyboard header and will be removed in future
builds, since the supplied keyboard cable makes it unnecessary.

## Connecting to the Amiga

1. Power off the Amiga.
2. Attach the mouse / joystick cable to the **P0** header on KeyJAM.
   Current firmware supports a single mouse/joystick port.
3. Attach the keyboard cable that matches your Amiga to the **Keyboard**
   header.
4. Plug the DB9 connector into the Amiga mouse port, and the keyboard
   connector into the Amiga keyboard port.
5. Plug your USB keyboard and USB mouse into the stacked USB-A ports.
6. Power on the Amiga.

Always power off the Amiga before connecting or disconnecting the
keyboard and joystick port cables.

## Power options

KeyJAM's 5V supply can come from any of these sources. The Amiga port
supplies are combined through Schottky diodes, so KeyJAM can be connected
to several at once.

| Source | How it connects |
| ------ | --------------- |
| Amiga keyboard port | Through the keyboard cable (diode D1) |
| Amiga mouse port (P0) | Through the P0 cable (diode D2) |
| Amiga joystick port (P1) | Through the P1 cable (diode D3) |
| USB-C | Install the **Type-C Direct Power** jumper |

The Amiga can't supply much current on its keyboard and joystick ports.
If you use power-hungry USB devices, such as RGB gaming keyboards,
wireless receivers, or USB hubs, power KeyJAM from a USB-C power supply.

## Jumpers

The jumpers are located immediately behind the USB-C port.

| Jumper | Installed | Removed |
| ------ | --------- | ------- |
| Type-C Data (two jumpers, D+ and D-) | USB-C data lines are connected to USB port 1. Required for firmware updates over USB-C, or to use the USB-C port as a USB host port. | USB-C data lines are disconnected. |
| Type-C Direct Power | KeyJAM 5V is powered from USB-C. | USB-C provides no power to KeyJAM. |

USB port 1 is shared between one of the stacked USB-A ports and the USB-C
port when the Type-C Data jumpers are installed. Don't plug devices into
both at the same time.

## LEDs

| LED | Meaning |
| --- | ------- |
| POWER | KeyJAM is powered and the firmware is running. |
| STATUS | Firmware status indication. |
| Keyboard | Flickers with keyboard clock activity to the Amiga. |
| P0_LED, P1_LED | Mouse / joystick port indication (firmware controlled). |
