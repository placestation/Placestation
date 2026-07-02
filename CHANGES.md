# Changes from upstream LumenPnP

This document describes every modification PlaceStation makes to the upstream LumenPnP v4 design. Unmodified upstream parts and software are not listed here — see [Opulo's LumenPnP repository](https://github.com/opulo-inc/lumenpnp) for those.

---

## 1. Sensorless homing (X/Y endstop hardware removed)

**Type:** Mechanical + Firmware modification
**Files:** `hardware/x-motor-mount/`, `firmware/marlin/`
**License:** CERN-OHL-W v2 (hardware), GPLv3 (firmware)

PlaceStation does not use physical X/Y endstop switches. Homing is achieved via the TMC stepper drivers' StallGuard (sensorless homing) feature. The benefits are:

- One fewer PCB to manufacture, stock, and ship per machine
- One fewer wiring harness from the X-motor area to the motherboard
- Simpler assembly with one less calibration step
- Fewer mechanical components to fail or get misaligned

The X-motor mount is modified to remove the cavity that originally housed the endstop PCB. This is a redesign of Opulo's `x-motor-mount` part.

The Marlin firmware is patched to enable StallGuard-based homing on X and Y. See [firmware/marlin/README.md](./firmware/marlin/README.md) for details (uploaded separately).

## 2. MGN12 linear rails throughout

**Type:** Mechanical modification
**Files:** `hardware/mgn12-x-gantry/`
**License:** CERN-OHL-W v2

The stock LumenPnP uses different linear rail sizes for the X gantry vs. other axes. PlaceStation uses **MGN12 rails throughout** the machine. This means:

- Consistent rail and carriage stock for self-builders (one part number for everything)
- Easier sourcing — MGN12 is widely available from MISUMI, AliExpress, and domestic Indian suppliers
- Simpler spares inventory

The X-gantry mount is redesigned to accept MGN12 rails. Adjacent mating parts may require minor adjustments depending on the carriage you choose.

## 3. Motherboard manufactured by TIPL (silkscreen debranded)

**Type:** PCB modification (silkscreen only)
**Files:** `pcb/mobo-REV05-debranded/`
**License:** CERN-OHL-W v2

PlaceStation ships with the `mobo-REV05` board originally designed by Opulo, **manufactured by Tejwani Industries Private Limited** under the CERN-OHL-W v2 license. The license allows commercial manufacturing of upstream hardware (CERN-OHL-W v2 §4.1).

**Silkscreen-only modification:** The Opulo wordmark and logo have been removed from the silkscreen layer. CERN-OHL-W v2 §8.2 specifically requires removal of upstream trademarks when redistributing under a different brand:

> "You shall not use any of the name (including acronyms and abbreviations), image, or logo by which the Licensor or CERN is known, except where needed to comply with section 3, or where the use is otherwise allowed by law."

**Unchanged:** Schematic, electrical layout, copper layers, drill files, BOM, component values, and functionality are identical to upstream `mobo-REV05`. This is **not** a redesign — it is a silkscreen-only debrand of Opulo's design, manufactured by TIPL.

A future version with a Raspberry Pi Compute Module (CM4) on the back of the motherboard for onboard OpenPnP execution is in development and will be released here when complete.

## 4. Datum board manufactured by TIPL (silkscreen debranded)

**Type:** PCB modification (silkscreen only)
**Files:** `pcb/datum-board-debranded/`
**License:** CERN-OHL-W v2

PlaceStation ships with the datum board originally designed by Opulo — the homing/calibration fiducial board that mounts to the primary staging plate — **manufactured by Tejwani Industries Private Limited** under the CERN-OHL-W v2 license.

**Silkscreen-only modification:** The Opulo wordmark and logo have been removed from the silkscreen layer, per the same CERN-OHL-W v2 §8.2 requirement described in section 3 above.

**Unchanged:** The homing fiducial dot, golden guideline squares, board outline, and all copper/drill geometry are identical to upstream. This is **not** a redesign, and calibration behavior (homing correction, mm/pixel calibration) is unaffected.

## 5. Dual-color printed secondary fiducial

**Type:** Mechanical modification (replacement for PCB-based part)
**Files:** `hardware/secondary-fid-dual-color/`
**License:** CERN-OHL-W v2

Opulo's stock secondary fiducial is a small PCB with a copper dot at center. PlaceStation replaces this with a **dual-color 3D-printed part**:

- Black PLA outer ring
- White PLA center dot
- Printed in a single dual-extrusion job — the white dot acts as the fiducial under bottom-camera vision

Eliminates one small PCB from the BOM, simplifies sourcing, and is more durable than a thin PCB if knocked.

## 6. OpenPnP closed-loop feeder calibration plugin

**Type:** Software modification (OpenPnP plugin)
**Files:** `software/openpnp/`
**License:** GPLv3 (inherited from OpenPnP)
**Companion repository:** https://github.com/ivishaltejwani/openpnp_feeder-closedloop

PlaceStation includes a custom OpenPnP plugin that adds **closed-loop pocket calibration** for Photon feeders. Stock OpenPnP relies on the mechanical accuracy of the feeder for pickup position — small drift, tape variation, or feeder shift causes pickup failures. This plugin uses bottom-camera vision to:

- Detect the actual position of the part in the feeder pocket
- Compute the offset from the expected position
- Apply that offset to the pickup command automatically
- Save the calibration per feeder

It is built on top of the [`press-play-walk-away` branch of OpenPnP](https://github.com/Jorropo/openpnp/tree/press-play-walk-away) by Jorropo, which itself adds closed-loop placement correction via bottom vision. PlaceStation's contribution extends that closed-loop approach to feeder pickup as well.

PlaceStation also ships a standalone **gear ratio calibration web tool** for finding the actual gear ratio of Photon feeder motors (used to patch the Photon firmware constant when motors don't match the hardcoded ratio). This is a separate browser-based tool that uses Web Serial and computer vision.

For full source, integration instructions, and the OpenPnP fork base, see the companion repository linked above and `software/openpnp/README.md`.

## 7. Custom Marlin firmware

**Type:** Firmware modification
**Files:** `firmware/marlin/` (sources uploaded separately)
**License:** GPLv3 (inherited from Marlin)
**Upstream:** [sphawes/Marlin](https://github.com/sphawes/Marlin), `rev05` branch

PlaceStation's Marlin firmware is forked from Opulo's `sphawes/Marlin` fork, `rev05` branch (the official LumenPnP firmware). PlaceStation modifications:

- **Sensorless homing on X and Y** (StallGuard-based, no endstop hardware needed)
- **Speed increment refinements** for smoother motion at higher feed rates
- Endstop pin definitions disabled in `Configuration.h`

Sources will be uploaded to `firmware/marlin/` shortly. Until then, the unmodified upstream `rev05` branch can be used as a baseline.

---

## What is NOT modified

For clarity, the following parts of LumenPnP are used **unchanged** in PlaceStation. They are not in this repository — see the upstream Opulo repo:

- Frame extrusion layout
- Y-gantry, Z-gantry assemblies (apart from MGN12 rail substitution)
- Mobo PCB electrical design (only silkscreen modified)
- Nozzle holder — PlaceStation uses a community design by Klingler/PapaJ ([Printables #1371646](https://www.printables.com/model/1371646)), not Opulo's stock holder. See CREDITS.md for attribution
- Bottom camera and lighting
- Vacuum system (pumps, valves, tubing)
- Feeders (Photon firmware and protocol)

---

## Component-level attribution chain summary

| Part | Original author | Used as-is or modified by TIPL? |
|------|----------------|-------------------------------|
| Frame, base, gantry | Opulo | Used as-is (MGN12 rail substitution) |
| `x-motor-mount` | Opulo | **Modified** (endstop cavity removed) |
| `mobo-REV05` | Opulo | **Modified** (silkscreen debranded) |
| Datum board | Opulo | **Modified** (silkscreen debranded) |
| Secondary fiducial | Opulo | **Replaced** (dual-color print instead of PCB) |
| Nozzle holder | Richard Klingler → PapaJ | Used as-is (community design, not Opulo's) |
| Marlin firmware | Marlin team → Opulo (sphawes) | **Modified** (sensorless homing + speed tweaks) |
| OpenPnP | OpenPnP project → Jorropo (press-play-walk-away) | **Extended** (closed-loop feeder calibration) |
| Photon firmware | Photon project | Used as-is (calibrated via TIPL's web tool) |
