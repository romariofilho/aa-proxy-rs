# Fork notes

This fork no longer carries code changes: everything it used to hold for the GAC Aion UT
was merged upstream (aa-proxy/aa-proxy-rs) on 2026-11-20:

- #146 `INSTRUMENT_CLUSTER_START` for the synthetic navigation channel (f228fbb)
- #147 HSP responder, "enhanced" SCO resampler, media-bridge start option, connect timeouts (ca36fbf..31a435c)

`main` here = upstream `main` + `docs/evidence/` (photos referenced by #146: Google Maps showing the
arrival battery % through the proxy). Older work branches (`bt-hsp-responder`, `aion-nav-status`, `pr/*`)
are historical and based on an outdated upstream; do not merge them.
