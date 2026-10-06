# TRIX (g_trix)

Status: **playable** — graphics, text, `.spr` animations, music, sound, help text, full rounds.
Facts: [notes/scaffold.md](notes/scaffold.md).

## Checklist
- [x] Window size 1280×800 matches the background
- [x] 0 unresolved symbols
- [x] Runs: attract mode, deal, contracts, card play
- [x] Paths resolve (assets under /usr/local/ion_only/games/g_trix; CWD = asset dir)
- [x] Translations + help text (translations/g_trix.utf8, SupportFiles.utf8)
- [x] Sound and music
- [x] Plays through with the profiler on (steady 30 fps)

## Known issues
- `gfx/hud/common_files/tricks` is not found (data quirk).
- One sound is requested with an empty name.
- Music track changes stall ~90 ms (whole OGG decoded at once) — stream it.
- First use of large `.spr` animations stalls 100–200 ms — cache/preload decoded frames.
- Card fanning (operator option) is off: its art is not shipped (`CARD_FANNING=1` to try).

## Log
- 2026-10-07 — First port. The bugs hit on the way (64-bit inode stat, static Translator,
  Pango modules, StopSound use-after-free, OGG length, ...) are in megatouch-port docs/reference/known-bugs.md.
- 2026-10-07 — Profiled a 100 s session: main thread 91% idle, ~4 ms/frame render+present,
  stalls only on first image loads and music track starts. 60 fps breaks game timing; stay at 30.
- 2026-10-07 — Moved into the template layout; re-scaffolded from the image with no manual steps.
- 2026-10-07 — Game-over screen and saved hi-score now come from shared fixes made for Word Dojo 2.
