# Alley Jam: audio sources

Every shipped audio file is listed with its source, author, license and modifications in
`data/audio_sources.json`. `godot --headless --path . -- --license-test` checks every file under `audio/` against that list.
There are no CC-BY-NC, no unclear licenses and no CC-BY files.

| Group | Files | License | Source |
|---|---|---|---|
| Kenney SFX (rim clank, bank, backboard rattle, shove, block, menu move/select, dunk slam*) | 8 | CC0-1.0 | kenney.nl Impact Sounds / Interface Sounds |
| Self-synthesized SFX (dribble, release, swish, short, pass, crossover, turbo, fire, buzzer, tip sting, steal, rim-out) | 12 | CC0-1.0 (own work) | `/workspace/audio-src/synth/make_sfx.py` (numpy) |
| Self-synthesized crowd (ambience loop, cheer, big cheer) | 3 | CC0-1.0 (own work) | same script |
| Announcer voice lines | 47 | Public Domain | Piper TTS, `en_US-norman-medium` voice |

\* dunk_slam = two Kenney impacts mixed with a synthesized 60 Hz boom.

**Kenney:** https://kenney.nl/assets/impact-sounds and https://kenney.nl/assets/interface-sounds. CC0 (License.txt in each pack). Credit is optional, but we give it anyway.

**Announcer:**
- Synthesized offline with Piper 1.8.0 (rhasspy). Piper is a GPL-3.0 tool, and that license doesn't cover its output audio.
- Voice: "norman" (medium) by Bryce Beattie, trained from scratch on about 15.5 h of LibriVox recordings. LibriVox recordings are public domain per the model card. Model repo: huggingface.co/rhasspy/piper-voices (MIT).
- Rejected voices:
  - "joe": fine-tuned from lessac, a non-commercial dataset.
  - "ryan" and "hfc_male": non-commercial datasets.
- Light processing:
  - silence trim
  - +3% rate
  - 100 Hz HPF
  - +3 dB at 3 kHz
  - 4:1 compression
  - 30 ms slap echo
  - limiter

**Format:** all files are mono, 22.05 kHz, OGG Vorbis. Total audio is about 836 KB on disk.
