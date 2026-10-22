# PLC-Based Motorized Garage Door Control System

A PLC-based automation project for controlling the opening and closing of a motorized garage door using push buttons, limit switches, ladder logic, and motor interlocking.

> **Project status:** Starter documentation — implementation and testing details should be updated as the project develops.

## Project Overview

This project is designed to automate garage-door movement with a Programmable Logic Controller (PLC). The operator uses separate OPEN and CLOSE push buttons. Limit switches detect the door's end positions, while interlocking logic prevents the opening and closing commands from being active simultaneously.

## Objectives

- Control garage-door opening and closing using a PLC.
- Use separate OPEN and CLOSE commands.
- Stop movement when the relevant end-position limit switch is reached.
- Implement holding (seal-in) logic where required.
- Implement electrical/ladder-logic interlocking between opposite directions.
- Document the ladder diagram, hardware, and test results.

## Proposed Hardware

- PLC compatible with the available programming environment
- OPEN push button
- CLOSE push button
- Open-position and closed-position limit switches
- Motor with suitable reversing contactors or motor driver, as appropriate
- Properly rated power supply and control wiring
- Overload protection and emergency-stop arrangement as required by the design

Confirm the final hardware list against the actual prototype before submission.

## Software

- MELSOFT GX Works3 (if using a compatible Mitsubishi PLC)
- PLC ladder-logic programming

## Working Principle

1. The operator presses OPEN to request opening.
2. The PLC energizes the opening command, subject to the closing interlock and the open-end limit condition.
3. The holding circuit can maintain the opening command after the momentary button is released.
4. The open-position limit switch stops further opening.
5. The operator presses CLOSE to request closing.
6. The PLC energizes the closing command only when the opening command is inactive and the closing-end limit has not been reached.
7. The closing-end limit switch stops further closing.

The exact contact polarity and rung logic must match the real push-button wiring, limit-switch type, and PLC input status.

## Control Logic Summary

| Function | Purpose |
|---|---|
| OPEN push button | Requests door opening |
| CLOSE push button | Requests door closing |
| Open limit switch | Stops opening at the open endpoint |
| Closed limit switch | Stops closing at the closed endpoint |
| Holding circuit | Keeps a command active after a momentary button press, until a stop condition occurs |
| Interlocking | Prevents opening and closing commands from being active together |

## Safety Notes

- Do not rely on PLC software interlocking alone for motor reversal.
- Use suitable hardware/electrical interlocking for reversing contactors.
- Provide correctly rated overload and short-circuit protection.
- Consider an emergency stop and obstruction detection appropriate to the application.
- Test the control logic without a connected motor first, then test with a safely isolated, protected setup under supervision.
- Never bypass limit switches or safety devices during normal operation.

## Project Files

As development progresses, add the following items to this repository:

- Ladder diagram screenshot/export from GX Works3
- I/O address table
- Hardware connection/wiring diagram
- Final project report
- Test cases and actual observations

## Testing Plan

| Test | Expected result |
|---|---|
| Press OPEN with no conflicting command and open limit not reached | Opening command activates |
| Release OPEN when holding logic is intended | Opening command remains active |
| Open limit is reached | Opening command turns off |
| Press CLOSE with no conflicting command and closed limit not reached | Closing command activates |
| Closing command is active | Opening command is blocked by interlock |
| Opening command is active | Closing command is blocked by interlock |
| Closed limit is reached | Closing command turns off |

Record the actual results only after performing each test on the prototype.

## Project Status

Starter documentation created. Hardware selection, final ladder logic, wiring, screenshots, and verified test results are to be added.

## Keywords

PLC, industrial automation, garage door control, ladder logic, limit switches, motor control, interlocking.

## Sustainable Development Goals

- **SDG 9:** Industry, Innovation and Infrastructure.
- **SDG 11:** Sustainable Cities and Communities.

