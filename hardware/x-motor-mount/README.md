# x-motor-mount

PlaceStation modification of the Opulo LumenPnP `x-motor-mount` part.

## What changed

The endstop PCB cavity has been removed. PlaceStation uses sensorless homing (TMC StallGuard) on X and Y, so the physical endstop switch and its housing are not needed.

## Files

| File | Format | Description |
|------|--------|-------------|
| `x-motor-mount.3mf` | 3MF | Print-ready file for FDM printing |

## Printing

Print in a rigid filament (PETG or ABS recommended). No supports needed. Use the same print settings as the upstream LumenPnP x-motor-mount.

## License

CERN-OHL-W v2 — see [`../../licenses/CERN-OHL-W-v2.txt`](../../licenses/CERN-OHL-W-v2.txt)

**Upstream:** Original `x-motor-mount` by Opulo Inc. ([github.com/opulo-inc/lumenpnp](https://github.com/opulo-inc/lumenpnp)), CERN-OHL-W v2. This file is a modified derivative.
