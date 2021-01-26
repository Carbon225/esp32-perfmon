# ESP32 CPU usage monitor
Gives you a **rough** idea of how the Xtensa cores are utilized.

Works by attaching idle hooks and measuring how often they get called.
The core usage is calculated: `usage% = idle ticks since last measurement / expected idle ticks if core were idle * 100%`.
The expected idle tick count was measured by running an empty program.

## Limitations:
- Should only be used for user information, not in logic that needs accurate values
- New IDF versions could optimize performance and therefore introduce an error to usage estimation.
- When one core is at 100% the other might report a negative value

## Usage:
- Download component into `<project_dir>/components/`
- `#include "esp32_perfmon.h"`
- Call `perfmon_start()` once
