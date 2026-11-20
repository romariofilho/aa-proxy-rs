# Evidence: Google Maps shows arrival battery % (EV routing) through aa-proxy-rs

Photos of the head unit of a GAC Aion UT running Android Auto through a Raspberry Pi 4
with this fork of aa-proxy-rs (`inject_navigation_status` + `INSTRUMENT_CLUSTER_START`).

In the Google Maps card, each suggested destination shows the **estimated battery
percentage on arrival** (battery icon next to the %), which Maps only displays when it
receives the vehicle's battery data:

| Photo | Time | Car SoC (right panel) | "Casa" (750 m) | Long trip (80-81 km) |
|---|---|---|---|---|
| `maps-battery-arrival-1.jpg` | 14:43 | 93.1 % | 92 % | 80 % |
| `maps-battery-arrival-2.jpg` | 14:10 | 85.1 % | 84 % | 72 % |

The arrival % tracks the car's current SoC minus the estimated consumption, in both photos.

Privacy: the map was blurred and the destination address pixelated; EXIF was stripped.
