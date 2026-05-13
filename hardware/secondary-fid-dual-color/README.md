# secondary-fid-dual-color

PlaceStation replacement for the Opulo PCB-based secondary fiducial — a dual-color 3D-printed part.

## What changed

Opulo's stock secondary fiducial is a small PCB with a copper dot at center. PlaceStation replaces it with a **dual-color 3D-printed part**:

- Black PLA outer ring
- White PLA center dot (acts as the fiducial target under bottom-camera vision)

Printed in a single dual-extrusion job. Eliminates one small PCB from the BOM and is more durable than a thin PCB if knocked.

## Files

| File | Format | Description |
|------|--------|-------------|
| `secondary_fid.f3d` | Fusion 360 | Full parametric CAD source |
| `IMG_0493.HEIC` | Photo | Reference image of finished part |

## Printing

Requires a dual-extrusion printer. Outer body: black PLA. Center dot: white PLA. No supports needed.

## License

CERN-OHL-W v2 — see [`../../licenses/CERN-OHL-W-v2.txt`](../../licenses/CERN-OHL-W-v2.txt)

This is an original TIPL design (not a modification of an Opulo part — it replaces a PCB with a printed alternative). Copyright (c) Tejwani Industries Private Limited.
