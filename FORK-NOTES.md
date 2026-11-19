# Fork notes — GAC Aion UT on a Raspberry Pi 4 (romariofilho/aa-proxy-rs)

What this fork carries on top of `aa-proxy/aa-proxy-rs`, why, and what was verified.

## Branches
- `aion-nav-status` — `inject_navigation_status` + the `INSTRUMENT_CLUSTER_START` fix.
- `bt-hsp-responder` — everything above plus the Bluetooth/HSP work.
- Clean PR branches on current upstream: `pr/cluster-start`, `pr/bt-hsp`.

## 1. Battery-on-arrival in Google Maps without a head-unit navigation service
The Aion UT (Desay SV IC2254/49, fw GACNE_AY2G_AVNT_S012_260513, Brazil) has services 1–12 and no
`navigation_status_service`, so Maps never sends `VehicleEnergyForecast` (0x8008). With
`inject_navigation_status` the proxy appends the service, answers the open locally and consumes the messages.
`INSTRUMENT_CLUSTER_START` must be sent after the open or Maps stays silent.
Verified: forecast events reach the websocket topic; Maps shows the arrival % for the destination;
SoC is fed by `POST /battery`. Without an `ev_model.bin` Maps uses the default (Ford) energy model.

## 2. Bluetooth / HSP
See the commit messages of the HSP commits: HSP responder, silent-downlink guard on the media bridge, connect backoff cap,
enhanced resampler, tunable per-attempt connect timeout.

## 3. Test notes
- Hardware: Pi 4 2 GB, S23 Ultra, Aion UT. Build for the Pi with the cross toolchain; local checks with
  `cargo check --no-default-features --features wasm-scripting` (io_uring accept hung on kernel 7.0 in our tests).
- MITM certificates must be present or the proxy falls back to passthrough and no forecast appears.
