# zlist releases

This repository is the public release channel for
[zlist](https://github.com/kindlyops/zlist). Download zlist from the
[releases page](https://github.com/kindlyops/zlist-releases/releases).

![zlist with the sample playlist open. PREVIEW shows the next cue. PROGRAM shows the camera.](docs/zlist.png)

## What zlist does

zlist plays a playlist into a virtual camera and a virtual microphone.
Zoom, and other meeting apps, can select these devices as a camera and a
microphone.

zlist opens two types of playlist:

- A `.jwlplaylist` export from JW Library.
- A build folder from `vbs plt build`.

Each item in the playlist is a cue. A cue is a video or a still picture.
When zlist opens a `.jwlplaylist`, it downloads the videos for the cues
from the media server. A video that is in the export plays without a
download.

When no cue plays, the virtual camera sends the picture from your camera.
The virtual microphone sends the sound from your microphone. When a cue
plays, the virtual camera sends the cue, and the virtual microphone sends
the sound of the cue.

The window has two monitors. PROGRAM shows what the virtual camera sends.
PREVIEW shows what goes to the meeting next. The meeting does not see the
monitors, the clocks, or the cue list.

You can control zlist in these ways:

- With the buttons in the window: Previous, Play, Stop, Next, and FTB
  (fade to black).
- With hotkeys that work from all apps.
- With the media keys on the keyboard.
- With OSC messages on UDP port 9000, for example from Bitfocus Companion.

The presentation timer measures the time of the full talk. The playlist
clock shows the time that is left in the cues.

Overlay mode makes the window smaller. A strip with the controls stays at
the top of the screen, and the cue list stays at the right edge. Then the
meeting app can use the other parts of the screen.

zlist has a sample playlist with title cards and color clips. To open it,
click **Open Sample Playlist** in the empty cue list.

## Install zlist on a Mac

zlist operates on macOS 14 or later, on Apple silicon and Intel Macs.

1. Download `zlist-<version>.zip` from the releases page.
2. Open the zip file.
3. Move `zlist.app` to the `Applications` folder. The virtual camera
   operates only from this folder.
4. Open zlist.
5. When macOS asks for access to the camera and the microphone, click
   **Allow**.
6. Click the **Camera** button in the toolbar of zlist.
7. In System Settings, go to General > Login Items & Extensions > Camera
   Extensions.
8. Turn on "zlist Camera".
9. In zlist, go to Settings > Audio.
10. Click **Install** to install the virtual microphone.
11. When macOS asks for your password, type it. The sound of the Mac stops
    for approximately one second.
12. In Zoom, select **zlist Camera** as the camera.
13. In Zoom, select **zlist Audio** as the microphone.

zlist gets updates from this repository. To get an update, click
zlist > Check for Updates.

## Install zlist on Windows

zlist operates on Windows 11. The Windows release does not have a signature
yet. Thus, Windows installs it only when Developer Mode is on.

1. Install VB-CABLE from <https://vb-audio.com/Cable/>. Zoom records the
   sound of zlist from this cable.
2. In Windows Settings, go to System > For developers.
3. Turn on **Developer Mode**.
4. Download `zlist-<version>-windows-x64.zip` from the releases page.
   If your computer has an ARM processor, download
   `zlist-<version>-windows-arm64.zip`.
5. Extract all the files from the zip file.
6. Open PowerShell in the extracted folder.
7. Type `powershell -ExecutionPolicy Bypass -File .\install.ps1`, then
   press Enter.
8. Open zlist from the Start menu.
9. When Windows asks for access to the camera and the microphone, click
   **Yes**.
10. Click the **Camera** button in the toolbar of zlist.
11. Click **Install**.
12. When Windows asks for administrator permission, click **Yes**.
13. In zlist, go to Settings > Audio > Send to.
14. Select **CABLE Input (VB-Audio Virtual Cable)**.
15. In Zoom, select **zlist Camera** as the camera.
16. In Zoom, select **CABLE Output (VB-Audio Virtual Cable)** as the
    microphone.

The Windows release does not get updates automatically. To install a new
release, do steps 4 to 8 again with the new zip file.

## Make sure that a download is correct

Each release has a `SHA256SUMS` file. This file has a SHA-256 checksum for
each file of the release.

1. Download `SHA256SUMS` into the folder that has your download.
2. On a Mac, type this command in Terminal, in that folder:
   `shasum -a 256 -c SHA256SUMS --ignore-missing`
3. Make sure that the output shows `OK` for your file.

## Contents of this repository

- Each release has `zlist-<version>.zip` (the Mac app), the Sparkle
  `.delta` updates, the Windows zip files, and `SHA256SUMS`. The Mac app
  has a Developer ID signature, and Apple notarized it.
- The `gh-pages` branch has the Sparkle appcast at
  `https://kindlyops.github.io/zlist-releases/appcast.xml`. The Mac app
  reads this appcast to find updates.
