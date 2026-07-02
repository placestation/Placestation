# PlaceStation

PlaceStation is a desktop pick-and-place machine for PCB assembly, manufactured by **Tejwani Industries Private Limited (TIPL)** in Maharashtra, India.

PlaceStation is a **derivative of the open-source [LumenPnP project by Opulo Inc.](https://github.com/opulo-inc/lumenpnp)** This repository contains the design source for all PlaceStation-specific modifications, released under the same open-source licenses as the upstream project.

If you are looking for the unmodified LumenPnP design files (frame, gantry, motherboard, feeders, etc.), please see the [upstream LumenPnP repository](https://github.com/opulo-inc/lumenpnp).

---

## What PlaceStation is

PlaceStation is sold as a finished pick-and-place machine for small electronics manufacturers, prototyping labs, and hardware startups in India and abroad. It is **based on LumenPnP v4** with the modifications listed below.

The PlaceStation product is sold commercially. The underlying design source — both upstream LumenPnP and the PlaceStation-specific modifications — is open source under CERN-OHL-W v2, GPLv3, and related licenses.

## Modifications in PlaceStation

For a detailed list see [CHANGES.md](./CHANGES.md). In brief:

1. **Sensorless homing (no endstop PCB)** — modified `x-motor-mount` removes the endstop cavity; X/Y endstop hardware is removed entirely; Marlin firmware patched for sensorless homing
2. **MGN12 linear rails throughout** — consistent rail size simplifies sourcing and assembly
3. **Motherboard manufactured by TIPL** — `mobo-REV05` design from Opulo, manufactured by TIPL with Opulo branding removed from silkscreen (license-compliant per CERN-OHL-W v2 §8.2)
4. **Datum board manufactured by TIPL** — Opulo's homing/calibration fiducial board, manufactured by TIPL with Opulo branding removed from silkscreen (same license-compliant debranding as the motherboard)
5. **Feeder PCB manufactured by TIPL** — Photon feeder board from Opulo, manufactured by TIPL with Opulo branding removed from silkscreen. This pass also inadvertently removed silkscreen artwork by Alethea "Stargirl" Flowers ([@theacodes](https://github.com/theacodes)) — see [CREDITS.md](./CREDITS.md#feeder-pcb-art-alethea-stargirl-flowers) for attribution
6. **Dual-color printed secondary fiducial** — replaces Opulo's PCB-based fiducial with a 3D-printed dual-extrusion part (black surround, white center dot)
7. **OpenPnP closed-loop feeder calibration plugin** — vision-based pocket calibration for Photon feeders, integrated into the `press-play-walk-away` branch of OpenPnP
8. **Custom Marlin firmware** — sensorless homing for X/Y plus speed-increment customizations

## Repository structure

```
.
├── README.md                        ← you are here
├── LICENSE                          ← umbrella license, points to per-component licenses
├── NOTICE                           ← attribution to all upstream projects
├── CHANGES.md                       ← detailed description of modifications
├── CREDITS.md                       ← all contributors and projects credited
├── licenses/
│   ├── CERN-OHL-W-v2.txt
│   ├── GPL-v3.txt
│   ├── MIT.txt
│   └── CC-BY-SA-4.0.txt
├── hardware/                        ← CAD modifications (CERN-OHL-W v2)
│   ├── x-motor-mount/
│   ├── mgn12-x-gantry/
│   └── secondary-fid-dual-color/
├── pcb/                             ← PCB modifications (CERN-OHL-W v2)
│   ├── mobo-REV05-debranded/
│   └── datum-board-debranded/
├── firmware/                        ← Firmware (GPLv3)
│   └── marlin/                      ← (placeholder, sources uploaded separately)
├── software/                        ← OpenPnP plugins and configs
│   └── openpnp/                     ← see also linked fork repository
└── reference/
    └── placestation-full-assembly/  ← Fusion exports of the whole machine (optional)
```

## How to buy a PlaceStation

Visit [placestation.in](https://placestation.in).

## How to build your own from this source

This repository contains only the **PlaceStation modifications**. To build a complete machine you also need the unmodified upstream LumenPnP files. The recommended flow is:

1. Clone the upstream LumenPnP repository: `git clone https://github.com/opulo-inc/lumenpnp`
2. Clone this repository: `git clone https://github.com/placestation/Placestation`
3. Use parts from the upstream repo unless this repo has a replacement for them
4. For firmware: see `firmware/marlin/README.md`
5. For software: see `software/openpnp/README.md`

We are a small team and cannot offer free build support. Commercial machines come with full assembly and support from TIPL.

## Licenses

This project uses multiple licenses for different components. See [LICENSE](./LICENSE) for the umbrella summary and [licenses/](./licenses/) for full license texts.

- **Hardware (CAD, PCB):** CERN-OHL-W v2
- **Firmware (Marlin fork):** GPLv3
- **Software (OpenPnP plugin):** GPLv3 (inherited from OpenPnP)
- **Software (PlaceStation tools and configs):** MIT
- **Documentation:** CC BY-SA 4.0

## Attribution

PlaceStation builds on the work of many open-source projects and individuals. See [CREDITS.md](./CREDITS.md) for the full list.

Particular thanks to:
- **Opulo Inc. / Stephen Hawes** for LumenPnP and the upstream Marlin fork
- **The OpenPnP project** and contributors, especially **Jorropo** for the `press-play-walk-away` branch
- **Richard Klingler** and **PapaJ** for the CP40 nozzle holder design
- **The Photon firmware project** for the Photon feeder protocol
- **Alethea "Stargirl" Flowers** ([@theacodes](https://github.com/theacodes)) for the original feeder PCB silkscreen artwork
- **The Marlin Firmware project** for the base firmware

## Contact

Tejwani Industries Private Limited
GSTIN: 27AALCT0935H1Z6
Maharashtra, India
Website: [placestation.in](https://placestation.in)
