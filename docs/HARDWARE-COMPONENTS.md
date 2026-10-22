# Proposed Hardware Components

This is a starter list for the PLC-Based Motorized Garage Door Control System. Confirm and update it to match the actual prototype before final submission.

| Component | Purpose |
|---|---|
| PLC | Executes the garage-door control ladder logic |
| OPEN push button | Requests opening |
| CLOSE push button | Requests closing |
| Open-position limit switch | Detects when the door reaches its open endpoint |
| Closed-position limit switch | Detects when the door reaches its closed endpoint |
| Motor | Moves the garage door |
| Reversing contactors or suitable motor driver | Controls motor direction, selected for the actual motor and PLC output interface |
| Power supply | Supplies the PLC, sensors, and control circuit as required |
| Overload and short-circuit protection | Protects equipment against electrical faults |
| Emergency-stop device and obstruction protection | Additional safety measures appropriate to the final design |
| Connecting wires and terminals | Provide control and power connections |

## Important implementation notes

- Verify PLC model, I/O voltage, output current rating, motor rating, and sensor wiring before wiring the system.
- Use hardware/electrical interlocking for reversing contactors; do not depend only on ladder logic.
- Confirm whether each input is ON or OFF when its push button or limit switch is activated. Ladder NO/NC contacts must match actual input states.
- Do not connect a motor directly to a PLC output unless the output and motor load are explicitly rated for that use.
