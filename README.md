# Bolometrix

**Temperature measurement and analysis for Optris infrared cameras, on Windows (and, without a
window, on Linux).**

Bolometrix turns an Optris infrared camera into a full thermal measurement station: a live
thermal picture with measure areas and alarms, recordings and snapshots, line scanning of moving
objects, several cameras joined into one picture, and a dual-range test that joins two cameras
into one temperature curve. It brings the functions of Optris's PIX Connect to the Optris Thermal
Camera SDK, and follows the SDK as Optris updates it.

Made by Derek Holzapfel. **Not an Optris product** — not made, sold or supported by Optris. Its
temperatures are computed by the Optris Thermal Camera SDK, which ships with it.

![The Operator view of Bolometrix](docs/guide/img/operator.png)

## What it does

- **Live measurement** — measure areas (rectangle, ellipse, point, polygon, freehand, profiles),
  hot and cold spot tracking, calculated objects, per-area emissivity and emissivity regions,
  objects found by temperature, and lengths and sizes in millimetres from the distance and the
  field of view.
- **Values you can trust** — the uncertainty of each value from Optris's stated accuracy, user
  calibration at several points (every corrected value marked "corr."), a verification log of
  readings against a reference, and the camera's health at a glance.
- **Alarms** — upper and lower limits with pre-alarms, shown in words and colour, that can set
  off a snapshot, a recording, or a process-interface output.
- **Three views** — Operator (watch the process), Engineer (set it up), and Overview (the shift
  at a glance, with a one-page PDF shift report).
- **Recording & snapshots** — radiometric recordings you can re-measure later, plain-video
  recordings, and radiometric TIFF / CSV / image snapshots, with a watermark if you like.
- **Exports, reports & batch work** — pictures, diagrams and recordings to Excel, MATLAB and
  HDF5; inspection reports from snapshots as PDF or Word; one setting applied to many snapshots
  at once.
- **Line scanning** — build a picture of a moving belt, sheet, or strip, line by line.
- **Merged pictures** — several cameras side by side, shown and measured as one picture.
- **Dual-range test** — two cameras in different ranges joined into one temperature curve; each
  test is saved with its data, a plot, and full metadata.
- **Interfaces** — the Optris process interface, PIX Connect-compatible remote commands over COM
  and TCP, a live web page with a QR code (it also offers the Android app when the app's file
  lies beside the program), a shared live picture, and a phone link.
- **Connections to other systems** — Modbus TCP and OPC UA servers for PLCs and SCADA, MQTT,
  e-mail (or text message) on alarms, an RTSP video stream, an AI link (MCP) for assistants, and
  one overview of several PCs. Each is off until you switch it on, listens only on the PC itself
  until you choose the network, and changes nothing unless you allow it.
- **The plant** — a long history (a year of values), process statistics (control limits, Cp and
  Cpk), recipes with lot numbers, user roles with an audit trail, and ready starts for common
  jobs.
- **Reach** — the window in English, German or Spanish; updates and error reports when you
  switch them on; network cameras found and set up with a guide; autofocus on your word.
- **Without a window** — Bolometrix for a server or a PC without a screen, on Windows and on
  Linux (x64 and arm64, with Optris's Linux SDK).

## Requirements

- Windows 10 or 11, 64-bit
- An Optris infrared camera (tested with the Xi 400)
- Nothing else — the parts of the Optris SDK the camera needs ship with Bolometrix. You do not
  install the Optris SDK or PIX Connect.
- Only for Bolometrix without a window: Microsoft's .NET 8 runtime (or newer); on Linux also
  Optris's SDK package for the system (Ubuntu 24.04 x64 or Debian 12 arm64). The Linux builds are
  `Bolometrix-<version>-linux-x64.zip` and `-linux-arm64.zip`; they are built but not yet tried
  on Linux.

## Install

1. Download `Bolometrix-<version>-Setup.exe` from the [Releases page][releases].
2. The files are unsigned, so Windows warns the first time. Choose **More info → Run anyway**,
   then **Yes** at the administrator prompt. IT departments can deploy the `.msi` instead — see
   `For IT departments.txt`.
3. (Optional) Check a download against `SHA256SUMS.txt`:
   ```powershell
   Get-FileHash -Algorithm SHA256 Bolometrix-<version>-Setup.exe
   ```

Then plug in the camera and open **Bolometrix** from the Start menu: a camera that is there when
the program starts is connected by itself. A camera plugged in later: choose it in the camera list
and click **Connect**.

## Network

As it comes, Bolometrix sends nothing over the internet by itself, with one exception: when a
camera needs calibration files that are not on the PC, the Optris SDK downloads them from Optris
(this can be switched off on the page Camera). When the PC lacks it, `Setup.exe` fetches
Microsoft's Visual C++ runtime from Microsoft.

Every network function is off until you switch it on, and one that listens (web page, remote
commands, Modbus TCP, OPC UA, the video stream) stays on the PC itself until you choose the
network. What you switch on sends only to what you enter: updates to GitHub (at most once a
day), MQTT to your broker, e-mail to your mail server, the overview of other PCs to their pages.
`For IT departments.txt` lists every port.

## Documentation

- **User's guide** (`User's guide.pdf`) — step-by-step, with pictures.
- **For IT departments** (`For IT departments.txt`) — silent installs, folders, every port.
- **Changelog** (`CHANGELOG.txt`) — what each version added.
- **Terms of use** (`Terms of use.txt`) — also under Help → Terms of use.
- **Notices** (`Notices.txt`) — the parts made by others that Bolometrix includes, and their
  licenses.

## Support

Questions and problems: **derekholzapfel@gmail.com**. In the program, **Help → Report a problem**
opens the log folder and says what to send.

---

Bolometrix is free to use and comes as it is, with no warranty. Its alarms and outputs help you
watch a process; they are not a safety system.

Copyright (c) 2026 Derek Holzapfel. All rights reserved.
Optris is a registered trademark of Optris GmbH & Co. KG; PIX Connect and Xi are product names of
Optris. QR Code is a registered trademark of DENSO WAVE INCORPORATED. Microsoft, Windows, Excel,
Word and .NET are trademarks of the Microsoft group of companies. MATLAB is a registered trademark
of The MathWorks, Inc. HDF5 is a trademark of The HDF Group. Modbus is a registered trademark of
Schneider Electric USA, Inc. OPC UA is a trademark of the OPC Foundation. Linux is the registered
trademark of Linus Torvalds in the U.S. and other countries. Ubuntu is a registered trademark of
Canonical Ltd. Debian is a registered trademark of Software in the Public Interest, Inc. Android
is a trademark of Google LLC. They are named here only to say what Bolometrix works with.

[releases]: https://github.com/derekownsall/bolometrix/releases