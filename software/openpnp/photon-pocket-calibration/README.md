# photon-pocket-calibration

PlaceStation OpenPnP plugin for closed-loop feeder pocket calibration.

## What it does

Adds vision-based pocket calibration for Photon feeders in OpenPnP. Instead of relying on mechanical feeder accuracy, the plugin:

1. Uses the bottom camera to detect the actual position of the part in the feeder pocket
2. Computes the offset from the expected position
3. Applies that offset to the pickup command automatically
4. Saves the calibration per feeder

Built on top of the [`press-play-walk-away` branch of OpenPnP](https://github.com/Jorropo/openpnp/tree/press-play-walk-away) by Jorropo, which adds closed-loop placement correction. PlaceStation's contribution extends that to feeder pickup as well.

## Source

The full plugin source lives in the PlaceStation OpenPnP fork:

**https://github.com/ivishaltejwani/openpnp_feeder-closedloop**

*(Transfer to the `placestation` org is pending.)*

## License

GPLv3 (inherited from OpenPnP) — see [`../../../licenses/GPL-v3.txt`](../../../licenses/GPL-v3.txt)

**Upstream:** OpenPnP ([github.com/openpnp/openpnp](https://github.com/openpnp/openpnp)), GPLv3. Press-play-walk-away branch by Jorropo ([PR #1914](https://github.com/openpnp/openpnp/pull/1914)).
