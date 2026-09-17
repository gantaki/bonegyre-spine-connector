# BoneGyre Spine connector

Press **Export** in [BoneGyre](https://bonegyre.app) — the effect opens in Spine.

The connector is a small program that watches the folder BoneGyre exports
into and, on every export, uses the Spine editor's own command line to build
a `.spine` project from the exported skeleton and `images/`, then opens it.
It runs the Spine you already have installed and licensed; nothing is
bundled, nothing talks over the network.

## Setup

1. **Download** the file for your system from the
   [latest release](../../releases/latest) and put it anywhere — the Desktop is fine.

   | System | File |
   |---|---|
   | Windows | `BoneGyre-Connector-win-x64.exe` |
   | macOS, Apple silicon | `BoneGyre-Connector-macos-arm64` |
   | macOS, Intel | `BoneGyre-Connector-macos-x64` |
   | Linux | `BoneGyre-Connector-linux-x64` |

2. **Double-click it.** A small window opens and stays open: it says where it
   found Spine and that it is watching `Documents/BoneGyre Exports` (created
   for you). Leave the window open while you work.

   First run only: Windows SmartScreen says "Windows protected your PC" —
   click *More info → Run anyway*. On macOS, right-click the file → *Open*.

3. **In BoneGyre:** Export → Output → **Save to: Folder on disk** → choose
   `Documents/BoneGyre Exports`. The panel now says *Spine connector running*.

4. **Press Export.** A few seconds later Spine opens with the project. Export
   again after every change; the project is rebuilt and reopened.

## Good to know

- Spine takes a few seconds per export — that is Spine starting.
- The generated `<project>.spine` is rebuilt from scratch on every export.
  Don't edit it in place: work in your own project and pull the effect in
  with File → **Import Project**.
- Spine never reloads an open project. Close the previous one before you
  export again, or open the fresh file from the folder.
- Spine installed somewhere unusual? The connector says so and stops. Set
  the `SPINE_LAUNCHER` environment variable to the launcher
  (`Spine.com` on Windows, `Spine.app/Contents/MacOS/Spine` on macOS,
  `Spine.sh` on Linux), or make a shortcut that passes `--spine "<path>"`.
- Spine imports data only into the version that exported it, so BoneGyre
  writes each export for the Spine that will open it: the connector lists
  your installed versions, BoneGyre opens the export in the newest one of
  the export's version (or the one you choose under *Save to → Open in*),
  and downloads a 3.x version through the launcher when you have none. If
  nothing fits, BoneGyre says so before you export and offers the matching
  version in one click. `--version 4.2.43` forces one.
- Run it with `--help` in a terminal for the other options (a different
  folder, a pinned Spine version, build-without-opening, run once).

## Requirements

- Spine (Essential or Professional), launched and activated on this machine.
- Chrome or Edge for BoneGyre's folder export.
