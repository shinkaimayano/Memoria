# DO NOT ORDER THIS

Several mistakes have been discovered since the original creation of this PCB that would make ordering this version a bad idea. Those being:

- The data pin for the aRGB indicator LEDs were not connected to the MCU in the schematic, forcing the user to bodge wire to the seperate breakout for it to function.
- QMK does not support using two seperate pins for aRGB, making seperate pins for indicators and one for underglow impossible to do.
- The routing of the data pins was poor.
  - They went through many unneeded vias.
  - Termination resistors were missing, making it out of spec.
    - In a later revision, they were added but the data pins were routed as if they weren't differental pairs and was routed decoupled in the end.
- Component usage and placement was poor and inconsistent.
  - Too many traces going near the crystal and one pad going to the capacitor uses a via.
  - GND via under the USB-C shield can cause issues if the mask was somehow scratched off.
  - Unplated switch holes added several unnecessary vias and made routing messier.
- The edge cuts could make it possibly incompatible with V3N due to the fillets smaller than the ones on the plate.

## Notes

- The libraries used for this project are [ai03's Switch Library](https://github.com/ai03-2725/MX_Alps_Hybrid), [ai03's Type-C Library](https://github.com/ai03-2725/Type-C.pretty), [ai03's Random Parts Library](https://github.com/ai03-2725/random-keyboard-parts.pretty), and [Keeb.io's Symbol Library](https://github.com/keebio/keebio-components) & [Keeb.io's Footprint Library](https://github.com/keebio/Keebio-Parts.pretty).
- You need at least KiCad 6 to open the source files.
