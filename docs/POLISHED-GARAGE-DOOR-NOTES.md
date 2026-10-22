# Motorized Garage Door Control — Polished Notes

## Problem Statement

A motorized garage door is operated by separate OPEN and CLOSE push buttons to prevent mechanical damage. The motor must stop automatically when the door is fully open or fully closed. The system must also prevent the opening and closing directions from being activated simultaneously.

## Sensor Conditions

### LS1 — Level Sensor 1 (Fully Open)

- Range: 0 to 100
- When LS1 = 100: fully open; the open-limit condition must stop the opening motor.
- When LS1 = 0: not at the fully open endpoint.

### LS2 — Level Sensor 2 (Fully Closed)

- Range: 0 to 100
- When LS2 = 0: fully closed; the closed-limit condition must stop the closing motor.
- When LS2 = 100: not at the fully closed endpoint.

> **Implementation note:** These are numerical sensor values. If LS1 and LS2 are analogue readings, use comparison instructions to create Boolean limit bits before using ordinary NO/NC ladder contacts. The conditions above describe the intended endpoint behavior; verify the actual sensor range and wiring.

## Ladder Logic Design

### Rung 1 — Opening motor M1

Conceptual logic:

`(OPEN OR M1 holding contact) AND NOT open-limit AND NOT M2`

- The OPEN push button starts the opening command.
- An M1 auxiliary NO contact in parallel with OPEN provides the holding (seal-in) function.
- The open-limit condition interrupts the rung when the door reaches fully open.
- An M2 auxiliary NC interlock prevents opening while the closing motor is active.
- The rung energizes M1.

### Rung 2 — Closing motor M2

Conceptual logic:

`(CLOSE OR M2 holding contact) AND NOT closed-limit AND NOT M1`

- The CLOSE push button starts the closing command.
- An M2 auxiliary NO contact in parallel with CLOSE provides the holding (seal-in) function.
- The closed-limit condition interrupts the rung when the door reaches fully closed.
- An M1 auxiliary NC interlock prevents closing while the opening motor is active.
- The rung energizes M2.

## Interlocking Explanation

- The M1 auxiliary NC contact in the closing rung blocks the closing command while M1 is active.
- The M2 auxiliary NC contact in the opening rung blocks the opening command while M2 is active.
- The holding contacts are NO auxiliary contacts of their respective commands and maintain the command after the push button is released, until a limit or interlock condition interrupts it.

## Important Contact-State Clarification

In PLC ladder logic, an NO instruction is true when its addressed bit is ON; an NC instruction is true when its addressed bit is OFF. This is separate from whether a physical field device is wired with a normally-open or normally-closed contact. Configure the ladder to match the real input states and use the actual sensor comparison bits.

## Safety and Testing

1. Verify both endpoint signals and their polarity in PLC monitoring.
2. Test the opening and closing interlocks with motor outputs isolated.
3. Confirm the motor stops at each endpoint.
4. Use suitable hardware/electrical interlocking for reversing contactors, plus correctly rated overload and short-circuit protection.
5. Include appropriate emergency-stop and obstruction protection for the application.
6. Record actual test results only after testing the real prototype safely.

**Note:** This document is a polished transcription of the supplied handwritten design. Confirm the exact hardware, addresses, sensor thresholds, and wiring before operating a real motor.
