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
