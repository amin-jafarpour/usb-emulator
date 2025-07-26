## USB Enumeration
- USB host detects, identifies, configures, and assigns resources to newly attached USB device.
- Pull-up resistor on D+ indicates full-speed and low-speed on D-. 
- USB host issues USB rest by pulling both D+ and D- low for 10ms. 
- USB device enters default state at address 0x00 upon receiving USB reset. 
- USB host sends the first GET_DESCRIPTOR request to address 0x00 to get 8-byte device descriptor. 
- The first GET_DESCIPTOR request determines VId, PID, class, subclass, protocol to find the right device driver.
- USB Host sends SET_ADDRESS request to address 0x00 to assign USB device a unique address. 
- USB device switches to the new addressed assigned to it. 
- USB Host sends the second GET_DESCRIPTOR request to determine device descriptor, configuration descriptor, string descriptors. 
- Configuration descriptor: interface and endpoint desciptors. 
- Host sends SET_CONFIGURATION request to choose one of the device’s available configurations.
- Device enters Configured State and is now ready to be used.



| USB State      | Description                                  |
| -------------- | -------------------------------------------- |
| **Attached**   | Just plugged in, passive                     |
| **Powered**    | VBUS detected                                |
| **Default**    | After reset, using address 0x00              |
| **Addressed**  | After receiving SET\_ADDRESS                 |
| **Configured** | After receiving SET\_CONFIGURATION           |
| **Suspended**  | No activity for >3ms, enters low-power state |



Time ────────────────────────────────────────────────────────────────────────▶

Host                      D+/D− Lines                     Device
│                             │                              │
│<── (1) Plug-in ─────────────┼──── Pull-up on D+ ─────────>│
│                             │                              │
│<── (2) Detect connection ───┼─────────────────────────────>│
│                             │                              │
│──> (3) Reset Bus (10 ms) ───┼──── D+/D− pulled LOW ───────>│
│                             │ <== Default State @ addr 0  │
│                             │                              │
│──> (4) GET_DESCRIPTOR(8) @ 0x00                            │
│                             ├──── Device responds with 8 B │
│                             │     of Device Descriptor     │
│                             │                              │
│──> (5) SET_ADDRESS(0x05) ─────────────────────────────────>│
│                             │ <== Device switches to addr  │
│                             │     0x05 after status stage  │
│                             │                              │
│──> (6) GET_DESCRIPTOR (full) @ 0x05                        │
│                             ├──── Full Device Descriptor   │
│                             │                              │
│──> GET_CONFIGURATION_DESCRIPTOR ──────────────────────────>│
│                             ├──── Config + Interface +     │
│                             │     Endpoint Descriptors     │
│                             │                              │
│──> GET_STRING_DESCRIPTOR(s)───────────────────────────────>│
│                             ├──── (Optional string info)   │
│                             │                              │
│──> (7) SET_CONFIGURATION(1) ──────────────────────────────>│
│                             │ <== Configured State         │
│                             │ Device ready for data xfer   │
