##### American Standard Code for Information Interchange (ASCII)
- Character encoding standard that represents text using numeric codes.
- Logical representation of characters and not hardware specific.
- Standard range [0, 127].
- Extended range [0, 255].

##### Scan Codes
- Numeric codes sent by a keyboard when a key is pressed or released.
- Hardware dependent.
- Make codes sent when key is pressed. 
- Break codes sent when key is released. 
- Set1, set2, set3. 
- Set1 is used by BIOS.

##### USB HID Codes
- Part of the USB HID (Human Interface Device) standard. 
- HID Usage Tables define codes for input devices (keyboards, mice, etc.).
- Codes are abstract, and independent of OS or hardware scan code sets.
- OS maps USB HID codes to scan codes, and scan codes to ASCII codes.

#### Modifier Keys
- Shift Key
- Control Key
- Alt Key
- Right Alt Key (AltGr)
- Command or ⌘ (MacOS)
- Function Key (Fn)
- Caps Key
##### Modifier Keys in USB HID 
- Modifier keys are bit flags in the HID report.
- The first byte of a USB HID keyboard report is reserved for modifier status.
- Keyboard sends modifier status byte along with up to 6 key usage codes.
| Bit | Modifier Key  |
|-----|---------------|
| 1   | Left Ctrl     |
| 2   | Left Shift    |
| 3   | Left Alt      |
| 4   | Power/cmd key |
| 5   | Right Shift   |
| 6   | Right Alt     |
| 7   | Right GUI     |
##### Modifiers in BIOS
- Modifier keys have their own scan codes like any other key.
| Hex Value | Key         |
|-----------|-------------|
| 0X2A      | Left Shift  |
| 0X36      | Right Shift |
| 0X1D      | Ctrl        |
| 0X38      | Alt         |




































--------------------------------------------------------------------------------

ATmega32u4

native USB communication

Adafruit

ICSP header

virtual (CDC) serial / COM port

32u4 or SAMD micro based boards


HID.h


 ASCII character codes to keyboard scan codes (technically, to USB HID
  Usage codes)

  keyboard with an ISO physical layout

  ANSI layout

  