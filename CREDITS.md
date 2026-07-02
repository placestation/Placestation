# Credits

PlaceStation builds on the work of many open-source projects and individuals. We acknowledge their contributions here with sincere gratitude — without their work, PlaceStation would not exist.

---

## Upstream hardware: LumenPnP by Opulo

PlaceStation is fundamentally a derivative of the **LumenPnP** project by **Opulo Inc.** The frame design, gantry geometry, motherboard, feeder protocol, motion architecture, and overall mechanical concept come from LumenPnP.

- **Project:** LumenPnP
- **Authors:** Opulo Inc. and the LumenPnP community
- **Lead:** Stephen Hawes ([@sphawes](https://github.com/sphawes))
- **Repository:** https://github.com/opulo-inc/lumenpnp
- **License:** CERN-OHL-W v2 (hardware), MPL 2.0 (CI workflows), CC BY-SA 4.0 (KiCad libraries)
- **Website:** https://opulo.io

Opulo's decision to release LumenPnP under a weakly reciprocal open hardware license is what makes commercial derivatives like PlaceStation possible. Thank you.

## OpenPnP and the press-play-walk-away branch

PlaceStation runs **OpenPnP** as its primary control software. We extend the **`press-play-walk-away` branch** by **Jorropo**, which adds closed-loop placement correction via bottom-camera vision — a substantial improvement over stock OpenPnP for production reliability.

- **Project:** OpenPnP
- **Repository:** https://github.com/openpnp/openpnp
- **License:** GPLv3
- **Website:** https://openpnp.org
- **Press-play-walk-away branch by Jorropo:** https://github.com/Jorropo/openpnp/tree/press-play-walk-away
- **PR #1914:** https://github.com/openpnp/openpnp/pull/1914

PlaceStation's own OpenPnP plugin (closed-loop feeder pocket calibration) is a derivative of OpenPnP and is licensed GPLv3. It lives at:
- https://github.com/ivishaltejwani/openpnp_feeder-closedloop *(transfer to `placestation` org pending)*

## Nozzle holder: Klingler → PapaJ

PlaceStation uses a community-designed nozzle holder, not Opulo's stock part. The chain:

**Richard Klingler** — original CP40 toolchanger geometry
- **Source:** https://github.com/richardklingler/openpnp/tree/master/openscad/toolchanger
- **License:** GPLv3 (via OpenPnP)

**PapaJ** — single-material remix with T-slot M3 hex bolt mounts
- **Source:** https://www.printables.com/model/1371646
- **Printables profile:** [@PapaJ_1388538](https://www.printables.com/@PapaJ_1388538)
- **License:** GPLv3 (inherited)

PlaceStation uses PapaJ's remix as-printed without modification. **No claim of authorship is made by TIPL for this part.**

## Marlin firmware

PlaceStation's firmware is forked from Opulo's fork of Marlin.

- **Marlin project:** https://github.com/MarlinFirmware/Marlin
- **License:** GPLv3
- **Opulo's fork (base for PlaceStation):** https://github.com/sphawes/Marlin, `rev05` branch

PlaceStation modifications (sensorless homing on X/Y, speed-increment refinements) are released under GPLv3 in `firmware/marlin/`.

## Photon feeder firmware

PlaceStation's feeders use the Photon firmware unmodified.

- **Project:** Photon Firmware
- **Repository:** https://github.com/photonfirmware/photon
- **License:** GPLv3

PlaceStation includes a separate **gear ratio calibration web tool** (in `software/openpnp/gear-ratio-tool/`) for measuring the actual gear ratio of Photon feeder motors that may differ from the firmware-hardcoded value. The tool is TIPL's own work, licensed MIT. It does not modify Photon firmware — it just produces the constant you patch in yourself.

## Feeder PCB art: Alethea "Stargirl" Flowers

The Photon feeder PCB silkscreen carries original artwork by **Alethea "Stargirl" Flowers** ([@theacodes](https://github.com/theacodes), [thea.codes](https://thea.codes/)), an open-source hardware/software creative technologist who has contributed to Opulo's ecosystem (including the Starfish RP2040 feeder control board).

- **Author:** Alethea "Stargirl" Flowers
- **GitHub:** https://github.com/theacodes
- **Website:** https://thea.codes/

When removing the Opulo wordmark/logo from the feeder PCB silkscreen (per CERN-OHL-W v2 §8.2, see `CHANGES.md` §5), this artwork was inadvertently removed from the same silkscreen layer along with it. **This was not intentional and is not a disavowal of the work** — TIPL makes no claim of authorship over this artwork and credits it here in full. We're documenting this openly and will restore the art to a future silkscreen revision.

## Tools and libraries

PlaceStation development uses:
- **OpenSCAD** — for SCAD-based parts (nozzle holder)
- **Autodesk Fusion 360** — for PlaceStation-original CAD parts (proprietary tool, files also exported in STEP for open-tool compatibility)
- **KiCad** / **EasyEDA Pro** — for PCB work
- **Web Serial API** — for the gear ratio calibration browser tool

---

## TIPL contributions

PlaceStation modifications, manufacturing, distribution, and support are by:

**Tejwani Industries Private Limited (TIPL)**
- Director & Founder: Vishal Tejwani
- GSTIN: 27AALCT0935H1Z6
- Maharashtra, India
- Website: https://placestation.in

TIPL's specific contributions to this repository:
- `x-motor-mount` modification (endstop cavity removed)
- MGN12 X-gantry mount design
- `mobo-REV05` silkscreen debrand (manufactured by TIPL)
- Datum board silkscreen debrand (manufactured by TIPL)
- Feeder PCB silkscreen debrand (manufactured by TIPL) — see attribution note above regarding Stargirl Flowers' artwork
- Dual-color secondary fiducial print
- OpenPnP closed-loop feeder pocket calibration plugin
- OpenPnP gear ratio calibration web tool
- Marlin firmware modifications (sensorless homing + speed tweaks)
- Documentation, assembly guides, and this open-source release

---

## Thanks

If you've contributed to any of the upstream projects above, your work is in every PlaceStation machine we ship. Thank you for keeping these projects open and welcoming.

If you find your name missing or an attribution incorrect, please open an issue at https://github.com/placestation/Placestation/issues — we will correct it promptly.
