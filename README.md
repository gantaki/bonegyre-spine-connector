# BoneGyre Spine connector

Press **Export** in [BoneGyre](https://bonegyre.app) — the effect opens in Spine.

The connector is a small app that watches the folder BoneGyre exports
into and, on every export, uses the Spine editor's own command line to build
a `.spine` project from the exported skeleton and `images/`, then opens it.
It runs the Spine you already have installed and licensed; nothing is
bundled, nothing talks over the network.

## Setup

1. **Install** the app for your system from the
   [latest release](../../releases/latest):

   | System | File |
   |---|---|
   | Windows | `BoneGyre Connector_<version>_x64-setup.exe` |
   | macOS, Apple silicon | `BoneGyre Connector_<version>_aarch64.dmg` |
   | macOS, Intel | `BoneGyre Connector_<version>_x64.dmg` |
   | Linux | `.AppImage` or `.deb` |

   First run only: Windows SmartScreen says "Windows protected your PC" —
   click *More info → Run anyway*. On macOS, right-click the app → *Open*.

2. **Open it.** A small window says where it found Spine, which versions
   are installed, and that it is watching `Documents/BoneGyre Exports`
   (created for you). Close the window — the connector stays in the tray.
   Turn on *Start with the system* to keep it there after a reboot.

3. **In BoneGyre:** Export → Output → **Save to: Folder on disk** → choose
   `Documents/BoneGyre Exports`. The panel now says *Spine connector running*.
   The folder is remembered on your account, for every project.

4. **Press Export** — or the timeline's **Open in Spine** button. A few
   seconds later Spine opens with the project; the tray icon pulses while
   it is on its way. Export again after every change; the project is
   rebuilt and reopened.

## Merge into your own project

Instead of a separate project beside the export, the effect can land inside
your `.spine` — merged into your skeleton, animations included:

1. In the connector window, **Add…** your `.spine` (or drop it on the
   window) and pick the Spine version you edit it in.
2. In BoneGyre, Export → Save to → **Spine project** → pick it. Your
   skeleton appears as a Spine Data layer in the viewport.
3. Close the project in Spine, press **Export**. The connector imports the
   merged skeleton into your project as a new skeleton and opens it.

Each export adds a fresh skeleton; delete the one you no longer want. The
connector re-reads the project whenever you save it.

## Good to know

- Spine takes a few seconds per export — that is Spine starting.
- Spine imports data only into the version that exported it, so BoneGyre
  writes each export for the Spine that will open it: the connector lists
  your installed versions, BoneGyre opens the export in the newest one of
  the export's version (or the one you choose under *Save to → Open in*),
  and downloads a 3.x version through the launcher when you have none. If
  nothing fits, BoneGyre says so before you export and offers the matching
  version in one click.
- The generated `<project>.spine` is rebuilt from scratch on every export.
  Don't edit it in place: work in your own project and pull the effect in
  with File → **Import Project**.
- Spine never reloads an open project. Close the previous one before you
  export again, or open the fresh file from the folder.
- Spine installed somewhere unusual? The window says *Not found* — pick the
  launcher with *Change…* (`Spine.com` on Windows,
  `Spine.app/Contents/MacOS/Spine` on macOS, `Spine.sh` on Linux).

## Requirements

- Spine (Essential or Professional), launched and activated on this machine.
- Chrome or Edge for BoneGyre's folder export.
