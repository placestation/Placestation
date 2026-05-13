# Marlin Firmware

PlaceStation Marlin firmware — forked from Opulo's `sphawes/Marlin`, `rev05` branch.

## Status

**Sources coming soon.** Firmware source files will be uploaded here shortly.

In the meantime, the unmodified upstream `rev05` branch can be used as a baseline:
- https://github.com/sphawes/Marlin/tree/rev05

## PlaceStation modifications

- **Sensorless homing on X and Y** — StallGuard-based homing via TMC stepper drivers; endstop pin definitions disabled in `Configuration.h`
- **Speed increment refinements** — smoother motion at higher feed rates

## Upstream

| Project | Repository | License |
|---------|-----------|---------|
| Marlin | https://github.com/MarlinFirmware/Marlin | GPLv3 |
| Opulo's fork (base) | https://github.com/sphawes/Marlin (`rev05` branch) | GPLv3 |

## License

GPLv3 — see [`../../licenses/GPL-v3.txt`](../../licenses/GPL-v3.txt)
