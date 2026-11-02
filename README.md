# Pro Audio Bridge

Pro Audio Bridge lets you use 64-bit Windows VST3 plug-ins in Bitwig Studio or REAPER
on Linux. You install a plug-in with the vendor's own Windows installer. The Bridge
sets up the Windows side for it and puts it in your DAW as a normal VST3 plug-in. You
never touch Wine.

This is a **closed beta**, by invitation only. You need a beta invite code to use it.
Nothing here is a finished product yet. Before you start, read the
[known issues](KNOWN_ISSUES.md).

## Download

1. Open the [latest release](https://github.com/kasselvania/pro-audio-bridge-releases/releases/latest).
   App releases are named after their version, such as `v0.9.0-beta.1`.
2. Download the installer for your system:

   | System | File name ends in |
   |---|---|
   | SteamOS (Steam Deck, in Desktop Mode) | `-steamos.install` |
   | CachyOS | `-cachyos.install` |
   | Fedora, Ubuntu | Not published yet |

3. Follow the [tester guide](TESTER_GUIDE.md). It covers installing, adding and
   activating a plug-in, updating, reporting a problem and uninstalling.

The installer checks the package's signature before it offers to install. Each
release also has a `SHA256SUMS` file, if you want to check the download yourself.

Releases named `runtime-…` hold Windows runtime parts and their source code. The app
downloads what it needs by itself. You don't need to download them.

## Updates

You run the installer only once. After that, the app updates itself:

- It looks for a new version when it opens, and once a day while it's open.
- It reads `latest.json` from the latest release here. That file is signed, and the
  app checks its signature before using it.
- When there is an update, the app says **Update available**. Click
  **Download and update**. The download is checked against the signed update before
  anything is installed.
- An update is meant to keep your plug-ins, projects and settings. The
  [known issues](KNOWN_ISSUES.md) say what has been seen so far.

Don't run a newer installer to update, unless the app tells you to.

## Reporting a problem

Use **Send a report** in the app. You can read every word of the report before it
goes, and you don't need a GitHub account. The app tells you your report's number.
If sending fails, save a copy from the same screen and send the file to your
invitation contact. The [tester guide](TESTER_GUIDE.md) shows how.

Please don't open issues here: this repository only holds downloads.

## Privacy

There is no telemetry. The app goes online to check for updates here, to download
its Windows runtime, and to send a report when you choose to. Your invite code stays
on your computer. Vendor sign-ins happen in the vendor's own window.

## Not affiliated

Pro Audio Bridge is an independent product. It is not affiliated with, endorsed by
or supported by Bitwig, Cockos (REAPER), Steinberg, Valve, Microsoft, CodeWeavers,
the Wine project, GloriousEggroll, or any plug-in or plug-in vendor.

VST is a registered trademark of Steinberg Media Technologies GmbH. Windows is a
trademark of Microsoft Corporation. Steam, Steam Deck and SteamOS are trademarks of
Valve Corporation. All other names are trademarks of their owners. They are used here
only to describe compatibility.
