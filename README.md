# qsx-catalog

Stream catalog for [QSX](https://github.com/rogue-soft/QSX) — the Apple TV
ham repeater streaming app. The app bundles a copy of `streams.json` and
refreshes from this repo's raw URL on launch, so feeds can be added or pruned
here without an app release.

Rules for entries:
- `streamURL` must be **https** and a direct audio stream (Icecast MP3/AAC or
  HLS) playable by AVPlayer — no web-player pages.
- Entries without a `streamURL` are directory-only; include
  `broadcastifyFeedID` where known so Premium subscribers can listen.
- Keep `id` values stable — favorites reference them.
- Brandmeister hose URLs (`wss://hose.brandmeister.network/spotter/?tg=N`)
  connect successfully for **any** TG number, even dead ones — a silent
  "waiting for traffic" card is indistinguishable from a working idle TG.
  Before pointing a card at a hose TG, verify it is real and carrying
  traffic: `curl https://api.brandmeister.network/v2/talkgroup/N` (a miss
  is a bad sign) and watch https://hose.brandmeister.network — the wall
  shows every TG with traffic network-wide. (Aug 2026: ECR's advertised
  TG 3129973 failed both while their reflector was live on Broadcastify;
  cross-network bridge TGs were largely purged from BM in 2021.)
