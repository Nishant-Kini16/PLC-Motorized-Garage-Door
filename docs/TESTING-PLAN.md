# Initial Testing Plan

**Status:** Planned tests. No results are claimed until the prototype has been tested.

| No. | Test | Expected result | Actual result |
|---:|---|---|---|
| 1 | Press OPEN while the door is not at the open limit and no close command is active | Opening command activates | To be recorded |
| 2 | Release OPEN when holding logic is intended | Opening command remains active | To be recorded |
| 3 | Activate the open-position limit switch | Opening command turns off | To be recorded |
| 4 | Press CLOSE while the door is not at the closed limit and no open command is active | Closing command activates | To be recorded |
| 5 | Activate the closed-position limit switch | Closing command turns off | To be recorded |
| 6 | Keep the opening command active and request closing | Closing command remains blocked by interlocking | To be recorded |
| 7 | Keep the closing command active and request opening | Opening command remains blocked by interlocking | To be recorded |
| 8 | Verify emergency-stop and protection devices, if included | The system enters the intended safe state | To be recorded |

## Test procedure and safety

1. Check the wiring, PLC input status, output assignments, and limit-switch polarity.
2. Test the ladder logic with motor outputs disconnected or safely isolated.
3. Verify interlocking and endpoint stopping before connecting the motor.
4. Conduct powered tests only with appropriate electrical protection and supervision.
5. Record actual observations, faults, and corrections in the final report.

Do not bypass limit switches, interlocks, overload protection, or emergency-stop devices during normal operation.
