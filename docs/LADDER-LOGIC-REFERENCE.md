# GX Works3 Ladder Logic Reference

The ladder screenshot for this project is intended to be stored as `images/gxworks3-ladder.png`.

## Address mapping (confirm against the actual PLC program)

| Address | Intended function |
|---|---|
| X0 | OPEN push button |
| X1 | CLOSE push button |
| X2 | Open-position limit input |
| X3 | Closed-position limit input |
| M0 | Opening command / internal relay |
| M1 | Closing command / internal relay |
| Y0 | Intended opening output |
| Y1 | Intended closing output |

These meanings are based on the project description and must be verified against the actual I/O wiring and GX Works3 device comments.

## Rungs visible in the supplied screenshot

1. **Opening command (M0):** X0 is in parallel with an M0 holding contact, followed by X2 and M1 logic contacts, driving coil M0.
2. **Closing command (M1):** X1 is shown as a contact in the command path with an M1 holding contact in parallel, followed by X3 and M0 logic contacts, driving coil M1.
3. **Y0 output:** An NC M0 contact drives Y0 in the screenshot.
4. **Y1 output:** An NO M1 contact drives Y1 in the screenshot.

## Verification notes

- In GX Works3, an NO ladder contact is logically true when its addressed device is ON; an NC ladder contact is logically true when its addressed device is OFF. Confirm the physical input state when each button or limit switch is actuated.
- If Y0 is the opening motor output, verify rung 3 carefully: an NC M0 contact means Y0 is commanded ON while M0 is OFF. This may not match the intended behavior.
- Confirm X2 and X3 correspond to the correct endpoints.
- Confirm the physical OPEN and CLOSE push-button wiring and input polarity.
- A software interlock is not a substitute for appropriate hardware interlocking, overload protection, and other required motor safety devices.

This file documents the screenshot, not a verified safety-certified control design. Validate all logic with the actual PLC and wiring before operating a motor.
