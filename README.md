# BoneGyre Connector for Spine

Export from [BoneGyre](https://bonegyre.app) — the effect opens in Spine.

The connector is a small app that watches the folder BoneGyre exports
into and, on every export, uses the Spine editor's own command line to build
a `.spine` project from the exported skeleton and `images/`, then opens it.
It runs the Spine you already have installed and licensed; nothing is
bundled, nothing talks over the network.

Opening exports in Spine comes with BoneGyre's **Solo and Studio** plans
([pricing](https://bonegyre.app/#pricing)). On Free, BoneGyre still writes
every export into the folder — you import it in Spine yourself.

## Setup

1. **Install** the app for your system from the
   [latest release](../../releases/latest):

   | System | File |
   |---|---|
   | Windows | `BoneGyre.Connector_<version>_x64-setup.exe` |
   | macOS, Apple silicon (*About This Mac* says *Chip: Apple M…*) | `BoneGyre.Connector_<version>_aarch64.dmg` |
   | macOS, Intel (*Processor: … Intel …*) | `BoneGyre.Connector_<version>_x64.dmg` |
   | Linux | `.AppImage` or `.deb` |

   First run only:
   - **Windows:** SmartScreen says "Windows protected your PC" — click
     *More info → Run anyway*.
   - **macOS:** drag the app to Applications and open it. If macOS won't
     open it, close the message, then go to System Settings → Privacy &
     Security, scroll down and click **Open Anyway** (it stays there for
     about an hour after the attempt) and confirm with your password.
     When it asks to access your Documents folder, click **Allow**: the
     exports land there.

2. **Open it.** A small window shows the Spine it found (*Spine 4.3.26*
   under its name) and the folder it watches, `Documents/BoneGyre Exports`
   (created for you). Close the window — the connector stays in the tray.
   To keep it there after a reboot, turn on *Start with the system* behind
   the gear.

3. **In BoneGyre:** Export → Output → **Send to: Spine** → choose
   `Documents/BoneGyre Exports`. The panel now says *Connector running*.
   The folder is remembered on your account, for every project.

4. **Press Open in Spine** — the export button says what the click will do —
   or the timeline's **Open in Spine**. A few seconds later Spine opens with
   the project; the tray icon pulses while it is on its way. Export again
   after every change; the project is rebuilt and reopened.

## Merge into your own project

Instead of a separate project beside the export, the effect can land inside
your `.spine` — merged into your skeleton, animations included:

1. In the connector window, **Add…** your `.spine` (or drop it on the
   window) — BoneGyre opens with it ready. The connector reads which Spine
   the project is saved in and works in that one, so your project stays in
   its version (shown under the project's ⟳ ✕ buttons); pick another there
   only to move the project on purpose.
2. Your skeleton is already a Spine Data layer in the viewport, and the
   export is already routed back into the project. (For a project added
   earlier: **Use in BoneGyre** beside it, or BoneGyre's Add menu →
   *From a Spine project*.)
3. Close the project in Spine, press **Open in Spine**. The connector
   imports the merged skeleton into your project as a new skeleton and
   opens it.

Each export adds a fresh skeleton; delete the one you no longer want. The
connector re-reads the project whenever you save it.

## Good to know

- Spine takes a few seconds per export — that is Spine starting.
- Spine imports data only into the version that exported it, so BoneGyre
  writes each export for the Spine that will open it: the connector lists
  your installed versions, BoneGyre opens the export in the newest one of
  the export's version (or the one you choose under *Send to → Spine → Open
  in*), and downloads a 3.x version through the launcher when you have none. If
  nothing fits, BoneGyre says so before you export and offers the matching
  version in one click.
- The generated `<project>.spine` is rebuilt from scratch on every export.
  Don't edit it in place: work in your own project and pull the effect in
  with File → **Import Project**.
- Spine never reloads an open project. Close the previous one before you
  export again, or open the fresh file from the folder.
- Clicked *Don't Allow* on macOS? The window says *No access to
  Documents*. Turn on *Documents Folder* under BoneGyre Connector in
  System Settings → Privacy & Security → Files and Folders. The connector
  carries on by itself; if it doesn't, quit it from the menu bar and open
  it again.
- Spine installed somewhere unusual? The window says *Spine not found* —
  click it (or the gear) and pick the launcher with *Change…* (`Spine.com`
  on Windows, `Spine.app/Contents/MacOS/Spine` on macOS, `Spine.sh` on
  Linux).

## Requirements

- Spine (Essential or Professional), launched and activated on this machine.
- Chrome or Edge for BoneGyre's folder export.

---

Spine is a trademark of Esoteric Software LLC. BoneGyre is not affiliated
with Esoteric Software.
