# Corrected Ladder Logic — Garage Door

This document provides the recommended **control logic reference** for the project. It is not a native GX Works3 project file. Recreate these rungs in GX Works3, verify the actual I/O wiring, then save and upload the genuine project file and screenshots.

## Assumed device mapping

| Device | Function |
|---|---|
| X0 | OPEN push button; ON while pressed |
| X1 | CLOSE push button; ON while pressed |
| X2 | Open-limit bit; ON when the door is fully open |
| X3 | Closed-limit bit; ON when the door is fully closed |
| M0 | Opening command / internal relay |
| M1 | Closing command / internal relay |
| Y0 | Opening motor/contactor command |
| Y1 | Closing motor/contactor command |

If your sensors are analogue 0–100 devices, do not use the analogue value directly as an ordinary NO/NC contact. First compare the analogue value to a threshold and create digital limit bits for X2 and X3 (or the actual assigned devices). Confirm that the stated end positions are mapped as assumed here.

## Rung 1 — Opening latch and interlocks

Logic equation:

`M0 = (X0 OR M0) AND NOT X2 AND NOT M1`

Build the rung as follows:
- Put X0 NO in parallel with M0 NO (holding/seal-in contact).
- After the parallel branch, place X2 NC (opens when open-limit bit X2 is ON).
- Then place M1 NC (blocks opening while the closing command is active).
- Drive coil M0.

## Rung 2 — Closing latch and interlocks

Logic equation:

`M1 = (X1 OR M1) AND NOT X3 AND NOT M0`

Build the rung as follows:
- Put X1 NO in parallel with M1 NO (holding/seal-in contact).
- After the parallel branch, place X3 NC (opens when closed-limit bit X3 is ON).
- Then place M0 NC (blocks closing while the opening command is active).
- Drive coil M1.

## Rung 3 — Opening output

Use an **M0 NO** contact to drive Y0:

`Y0 = M0`

The earlier screenshot showed an M0 NC contact before Y0. If Y0 is the opening output, that is inverted and should be changed to M0 NO.

## Rung 4 — Closing output

Use an **M1 NO** contact to drive Y1:

`Y1 = M1`

## End-limit behavior

- At fully open, X2 must become ON; its NC ladder contact opens and resets/stops M0.
- At fully closed, X3 must become ON; its NC ladder contact opens and resets/stops M1.
- Confirm these ON/OFF states in GX Works3 monitoring before connecting the motor.

## Important note about sensor states

Your handwritten notes describe LS1 as 0–100 with fully open at 100, and LS2 as 0–100 with fully closed at 0. These appear to be analogue values or scaled sensor readings. A standard ladder contact operates on a Boolean device state, not directly on a numerical value. Use comparison instructions or a suitable sensor/controller to produce the digital limit bits, and choose thresholds based on the actual sensor and mechanical setup. The bit mapping above is an assumption that must be verified.

## Safety

- Keep electrical/hardware interlocking between reversing contactors in addition to PLC interlocking.
- Use correctly rated motor drive/contactors, overload and short-circuit protection, and appropriate emergency-stop/obstruction protection.
- Test logic with motor outputs isolated first. Do not bypass limit switches or safety devices.
- Never treat this reference as a substitute for checking the real wiring, device addresses, and PLC model.
