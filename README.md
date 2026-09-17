# Nimbo — Image Organizer

Nimbo sorts a whole drive (or any folder) of photos into a clean, dated
folder structure. It reads EXIF/XMP capture dates straight from file
headers, detects screenshots and numbered dataset sequences, finds exact
and near-duplicate images, and moves/copies everything with a full undo
journal — nothing is touched until you approve the plan.

**This repository ships a ready-to-run Windows build. No Python
installation, no dependencies, no setup — download and run.**

## Download

Get the latest `Nimbo.exe` from the [Releases page](../../releases/latest).

Windows SmartScreen may warn because the build isn't code-signed yet —
click **More info → Run anyway**.

## Features

- **Two-phase workflow** — scan builds a plan first, apply executes it and writes an undo journal.
- **Date detection** — EXIF/XMP header parsing, filename dates, epoch timestamps, and file-modified-time fallback.
- **Screenshot detection** — recognized and routed into their own folder, optionally split by year.
- **Numbered-sequence detection** — folders full of dataset-style filenames are recognized so bare digits aren't mistaken for years.
- **Duplicate detection** — exact duplicates via content hashing, plus optional GPU-accelerated near-duplicate detection when available.
- **Flexible destination structure** — `year`, `year-month`, or `year-month-flat` folders.
- **Safe by default** — collision handling, sidecar file support (`.xmp`, `.aae`, etc.), and a reversible undo journal for every run.

## Privacy

Nimbo makes no network calls of any kind — there is no telemetry, no
update check, no analytics, nothing sent anywhere. It only reads and
moves files on the drives you point it at.

Two small local files are written, both stay on your own machine:

- `%USERPROFILE%\.nimbo\settings.json` — remembers your last-used
  options so the app opens the way you left it.
- `<destination>\.nimbo\journal-*.jsonl` — a per-run undo log so
  "Undo last run" can reverse a move/copy.

Closing the window cancels any in-progress run and terminates the
process immediately — nothing keeps running in the background.

## License

All rights reserved. See [LICENSE](LICENSE). Source code is closed and
not distributed — only the compiled application is published here.
