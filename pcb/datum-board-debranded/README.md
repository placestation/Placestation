# datum-board-debranded

PlaceStation datum board — Opulo's LumenPnP homing/calibration fiducial board, manufactured by TIPL, with Opulo branding removed from the silkscreen layer.

## What it is

The datum board mounts to the LumenPnP's primary staging plate and provides the machine's optical homing fiducial. Nearly every calibration (homing correction via `ResetToFiducialLocation`, top-camera mm/pixel calibration via the golden guideline squares) is referenced against this board, so its fiducial and guideline geometry must match upstream exactly.

## What changed

**Silkscreen only.** The Opulo wordmark and logo have been removed from the silkscreen layer per CERN-OHL-W v2 §8.2, which requires removal of upstream trademarks when redistributing under a different brand.

The homing fiducial dot, golden guideline squares, board outline, and all copper/drill geometry are **identical to upstream**. This is not a redesign — calibration behavior is unaffected.

## Files

| File | Format | Description |
|------|--------|-------------|
| `gerbers/` | Gerber (RS-274X) + Excellon drill | Fabrication-ready gerbers, drill file, flying-probe test points, and ordering notes, as exported for manufacturing |

## Manufacturing

This board is manufactured by Tejwani Industries Private Limited (TIPL) under the CERN-OHL-W v2 license, which explicitly permits commercial manufacturing of covered hardware (§4.1).

## License

CERN-OHL-W v2 — see [`../../licenses/CERN-OHL-W-v2.txt`](../../licenses/CERN-OHL-W-v2.txt)

**Upstream:** Datum board originally designed by Opulo Inc. as part of [LumenPnP](https://github.com/opulo-inc/lumenpnp) ([product page](https://www.opulo.io/products/lumenpnp-datum-board)), CERN-OHL-W v2. This file is a silkscreen-only derivative.
