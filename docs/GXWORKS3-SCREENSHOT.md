# GX Works3 Program

This folder is intended to contain the latest GX Works3 ladder screenshot for the garage-door control project.


The screenshot should show these four rungs:
1. Opening command latch: `(X0 OR M0) AND NOT X2 AND NOT M1 -> M0`
2. Closing command latch: `(X1 OR M1) AND NOT X3 AND NOT M0 -> M1`
3. Opening output: `M0 NO -> Y0`
4. Closing output: `M1 NO -> Y1`

## Uploading the screenshot

The screenshot itself must be uploaded as an image file through GitHub's **Add file → Upload files** workflow. This document does not contain the binary screenshot.

Before running a real motor, verify that X2 is ON at fully open and X3 is ON at fully closed. If LS1/LS2 are analogue 0–100 sensors, use comparison logic to generate digital limit bits. Verify all I/O mappings, hardware interlocking, and safety protections.
