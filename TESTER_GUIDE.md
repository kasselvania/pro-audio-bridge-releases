# Pro Audio Bridge — tester guide (closed beta)

Pro Audio Bridge lets you use 64-bit Windows VST3 plug-ins in Bitwig Studio or REAPER
on Linux. It sets up and runs the Windows side for you. You never touch Wine.

This guide uses the words you will see on screen. It calls the product "the Bridge".
Read [KNOWN_ISSUES.md](KNOWN_ISSUES.md) before you start. Try the Bridge on a copy of
a project first, not on a session you can't afford to lose.

## Where the beta stands

The first signed release, `0.9.0-beta.1`, came out on 2 November 2026. On a clean
Steam Deck it was seen to install from its installer, accept an invite, add u-he
TyrellN6 through u-he's own installer, play it in Bitwig, keep a changed setting
after saving, quitting and reopening, restart it after it stopped, and send a report.
Here is what has and hasn't been seen, on that release and on earlier test builds:

- **Steam Deck (SteamOS) with Flatpak Bitwig.** Seen: install, adding plug-ins,
  hearing them, save and reopen, reboot, and updating from the app. Serum 2 was
  activated there and Kontakt 8 came through Native Access.
- **CachyOS with REAPER.** Seen on earlier test builds in a virtual machine: install,
  adding a plug-in, rendered sound, save and reopen, reboot and update. That machine
  has no speakers, so nobody has heard it live on CachyOS yet. The CachyOS installer
  of `0.9.0-beta.1` is the same file as the SteamOS one, but it hasn't been tried on
  CachyOS yet.
- **Fedora and Ubuntu.** There is no installer for them yet. Nothing has been checked.
- **REAPER on SteamOS, Bitwig on CachyOS.** Not checked yet.
- **Sending a report from the app** works: one was sent from `0.9.0-beta.1`.

## What you need

- An x86-64 computer with SteamOS (Steam Deck in Desktop Mode), CachyOS, Fedora or
  Ubuntu. Fedora and Ubuntu need an installer that isn't published yet.
- Bitwig Studio or REAPER. Other Linux VST3 DAWs may work, but nobody has tried them.
- The vendor's Windows installer for your plug-in (`.exe` or `.msi`), or their
  installer app, such as Native Access.
- An internet connection. The Bridge downloads its own Windows runtime.
- Your beta invite code. It comes to you privately. Don't share it.

You don't need Wine, Proton, Steam or a compiler. Today you only need a terminal to
uninstall.

## 1. Install the Bridge

1. On a Steam Deck, switch to Desktop Mode first.
2. Open the download link from your invitation. Download the file for your system:
   the one ending in `-steamos.install` for SteamOS, or `-cachyos.install` for CachyOS.
3. In your file manager, right-click the file and open **Properties**. Under
   **Permissions**, turn on **Is executable**.
4. Double-click the file. Choose **Execute** if asked.
5. A window called **Install Pro Audio Bridge** checks the file's signature. Click
   **Install application files**, then **Open Setup**.
6. In **Pro Audio Bridge Setup and Updates**, click **Set up application**, then
   **Start bridge service**.
7. Open **Pro Audio Bridge** from your applications menu.
8. It says **Enter your beta invite code**. Paste your code and click **Accept invite**.
   The code is checked on your computer and never sent anywhere.

You run the installer only once. Every later update happens inside the app.

Opening the installer by double-clicking it has not been checked yet; test runs
started it from a terminal. If double-clicking does nothing, tell your invitation
contact. Meanwhile, you can start it from a terminal. If you saved it in Downloads
and use SteamOS, paste this (use `cachyos` instead of `steamos` on CachyOS):

```sh
cd ~/Downloads && chmod +x ./*-steamos.install && ./*-steamos.install
```

## 2. The Bridge window

The column on the left has four pages: **Plug-ins**, **Activity**, **Setup** and
**Diagnostics**. At its foot you'll find the Bridge's own status, a line about an
update when there is one, and **Send a report**.

Each plug-in shows one word:

- **Ready**: it's in your DAW.
- **Needs you**, or **Stopped**: something needs you. Open it to see what and why.
- **Setting up**, **Checking** or **Waiting**: the Bridge is busy. Wait.
- **Unknown**: the window has no current status yet. The word changes when status
  comes back.

## 3. Add a plug-in

1. On **Plug-ins**, click **Add your first plug-in**. Later, use **Setup**.
2. On **Setup**, click **Choose Windows installer** and pick the vendor's file.
3. Click **Install and connect to your DAW**. When it asks which DAW you use, choose
   **Bitwig**, **REAPER** or **Another Linux VST3 DAW**.
4. Click **Start installation**. The first time, the Bridge downloads its Windows
   runtime. This can take several minutes.
5. The vendor's installer opens in its own window. If it asks, choose VST3 and
   64-bit. Finish it as you would on Windows.
6. The Bridge then finds and connects the plug-ins by itself. Each one shows
   **Ready** on **Plug-ins** when it's in your DAW.

**Vendor apps such as Native Access.** Pick the app's installer in step 2. The app
opens in its own window. Sign in and install your products there. When you're done,
close the app normally, or press **Stop** for it on **Setup**. The Bridge then
connects what you installed. On the Steam Deck this took about a minute. To install
more later, open one of its plug-ins and click **Add plug-ins through Native Access**.

## 4. Activate your plug-in

Your licence stays between you and the vendor. The Bridge never reads, copies or
changes it.

- Activate in the vendor's own window: their installer, their app, or the plug-in's
  own window in your DAW. Some plug-ins open a browser page to sign in.
- The browser page may open behind your other windows. Look for it in the taskbar.
- Right after you sign in, Native Access may say it couldn't load your products.
  Wait a minute, then try again in Native Access.
- Many vendors limit how many computers you can activate. Activate only where you
  need to.

So far, only the maintainer has activated plug-ins through the Bridge, on test builds.

## 5. Use it in Bitwig or REAPER

1. Open your DAW. Your plug-ins appear as VST3 plug-ins under their normal names.
   If one is missing, rescan VST3 plug-ins in your DAW's settings.
2. Add it to a track. Play some notes or audio. Open its window.
3. Save, quit the DAW completely, and reopen the project. Check that the sound and
   settings came back. This is the most useful single check you can do for us.

**Flatpak Bitwig (the Steam Deck way).** Bitwig runs in a sandbox. The Bridge gives
it the one permission it needs to reach the Bridge, by itself. Don't change Bitwig's
Flatpak permissions yourself.

**What the plug-in's page tells you.** It shows what the Bridge really saw. For
example, **Playing** means its sound was seen just now. "Loaded, no sound right now"
means it's loaded but silent. This is measured where the sound leaves the plug-in,
not at your speakers.

## 6. Update the Bridge

The app looks for updates when it opens, and once a day while it's open.

1. When there's an update, the foot of the left column says
   **Update available:** and the version. Click **View update**. You can also open
   **Setup** and choose **Pro Audio Bridge** under **Bridge**.
2. Read **What's new**.
3. Save your project and close your DAW.
4. Click **Download and update**. The download is checked against the signed update
   before anything is installed.
5. If your DAW is still using a bridged plug-in, the update waits. It continues by
   itself once you close the DAW. **Cancel** stops waiting.
6. Setup finishes the update. Then the app says **Updated to** the new version.

**Check for updates** checks right now. If the app asks for a beta link, paste the
one from your invitation and click **Save beta link**. You only do this once.

Your plug-ins, projects and settings are kept. If an update fails, the app says
"Couldn't update to …; still on …. The previous version was kept."

Don't download and run a new `.install` file to update, unless the app tells you
to. Never open an older `.install` file: it can take you back a version (see
[KNOWN_ISSUES.md](KNOWN_ISSUES.md)).

Updating from the app has been seen on the Steam Deck with a test update feed. The
public update feed is live with `0.9.0-beta.1`; the first update through it comes with
the next release.

## 7. When a plug-in stops

If a plug-in's Windows side stops while you use it, your DAW keeps showing the
plug-in as if nothing happened, but its track goes silent. The Bridge tells you:

- A desktop notification says "*Plug-in* stopped. Its track in your DAW is silent.
  Open the Bridge window and press Restart."
- In the Bridge, on **Plug-ins**, "*Plug-in* stopped" sits under **Needs you**, and
  the plug-in itself says **Stopped**.
- If you open the plug-in's own window in your DAW, it says "This plug-in stopped.
  Its track is silent."

A plug-in that couldn't load at all shows **Plug-in not loaded** in its window
instead, with the reason.

What to do:

1. If you can, don't save over your project yet. Changes made after the plug-in's
   last confirmed settings may be missing.
2. Open the Pro Audio Bridge window. On **Plug-ins**, click "*Plug-in* stopped"
   under **Needs you**, then **Open plug-in recovery**. Read what it says happened.
3. Click **Restart this plug-in**. It asks **Restart this plug-in instance?** and
   names the saved state it will bring back. Click **Restart from confirmed state**.
   The plug-in comes back in your DAW with those settings. You don't need to reload
   anything in your DAW, and the notification closes.
4. Check its sound and settings, then save.
5. If the window said **Plug-in not loaded**, do what it says: reopen the project or
   restart your DAW. If the plug-in's page in the Bridge offers a button to fix it,
   use that button.
6. If it still won't work, click **Send a report about** the plug-in on its page.

If the DAW already saved after the stop, **Plug-ins** says the plug-in "was saved
with its last confirmed state". Click **Open plug-in recovery** and follow it.

Restart was seen working with Serum 2 in Bitwig on the Steam Deck, on test builds.
It hasn't been tried in REAPER, or while other plug-ins play in the same project.

## 8. Report a problem

1. Click **Send a report** at the foot of the left column. Or, on a plug-in's page,
   click **Send a report about** that plug-in.
2. Under **About**, choose the plug-in, or **Something else**.
3. Under **What happened?**, write what you did, what you expected and what happened.
   Name your DAW.
4. **What's included** lists what goes with it: your words with private details
   removed, the Bridge's version, your Linux, your DAW and runtime, and how your
   setups and plug-ins are doing. It never includes licences, accounts, other
   plug-in names or your files.
5. To read every word first, open **See exactly what's included** and click
   **Show the exact report**.
6. Click **Send report**. When it arrives, the app says "Sent. Your report is" and
   gives you a number. You don't need a GitHub account.

If sending fails, click **Save a copy instead…** and choose where to save the file.
Nothing is sent. Then send that file to your invitation contact.

Never type passwords, serial numbers, licence keys or account names into a report.

## 9. Sample libraries on another drive

If a plug-in's library lives on an SD card or another drive:

1. Open the plug-in on **Plug-ins**, then **Sample locations**.
2. Click **Add a library folder…** and pick the folder. Choose **Read-only**, unless
   the plug-in needs to write there (**Read and write**).
3. **Remove folder access** takes the access away. Your files stay where they are.

Adding a folder has been seen working, but no plug-in has been seen reading samples
through it yet.

## 10. Uninstall

There is no one-click uninstall yet.

1. **Licences first.** If a vendor limits how many computers you can activate,
   deactivate the licence in the vendor's app or plug-in now. Deleting files doesn't
   give an activation back.
2. **Projects.** In your DAW, take bridged plug-ins out of any project you want to
   keep using without the Bridge, and save.
3. **Setups.** In the Bridge window, open **Setup**. Open each installer listed under
   **Installers**, click **Delete this setup**, read what it deletes, then click
   **Delete setup**. This deletes everything installed in that setup, and any
   licences, sign-ins or presets kept inside it. Your project files are not changed.
4. **The Bridge.** Close the Bridge window and your DAW. Open a terminal (Konsole on
   the Steam Deck) and paste all of this:

   ```sh
   bash -c '
   systemctl --user disable --now linux-vst-bridge.service
   rm -f ~/.config/systemd/user/linux-vst-bridge.service
   systemctl --user daemon-reload
   rm -f ~/.local/bin/linux-vst-bridge ~/.local/bin/linux-audio-compatibility-manager
   rm -f ~/.local/share/applications/linux-audio-compatibility-manager.desktop \
         ~/.local/share/applications/linux-vst-bridge-*.desktop \
         ~/.local/share/applications/linux-audio-bridge.desktop \
         ~/.local/share/applications/steam_app_linux-audio-bridge*.desktop
   rm -f ~/.local/share/icons/hicolor/scalable/apps/linux-audio-bridge.svg \
         ~/.local/share/icons/hicolor/*/apps/pab-*.png
   rm -rf ~/.local/share/linux-vst-bridge ~/.vst3/LVB_*.vst3
   [ -f ~/.config/mimeapps.list ] && sed -i "/^x-scheme-handler\/native-access=linux-vst-bridge-native-access\.desktop;\?$/d" ~/.config/mimeapps.list
   true
   '
   ```

   This removes everything the Bridge stored, including any setup you didn't
   delete in step 3.
5. **Flatpak Bitwig.** The Bridge gave Flatpak Bitwig one permission,
   `xdg-run/linux-vst-bridge`. It doesn't take it back by itself yet. Remove it:

   ```sh
   flatpak override --user --nofilesystem=xdg-run/linux-vst-bridge com.bitwig.BitwigStudio
   ```

   Nothing else of Bitwig's is changed. To see Bitwig's permission changes, run
   `flatpak override --user --show com.bitwig.BitwigStudio`. Don't use `--reset`
   unless you made no other changes to Bitwig yourself: it removes all of them.
6. Restart your computer.

These steps now include the menu entries and icons that an earlier version of this
guide left behind. They haven't yet been checked by reinstalling afterwards.

## What is and isn't collected

- **Nothing is sent by itself.** There is no telemetry.
- **Update checks** download signed update information and installers from the
  public releases page. They carry no account data.
- **The Windows runtime** downloads from its publishers (GE-Proton and the Steam
  Linux Runtime) and from the public releases page.
- **Reports** go only when you send or save them, and you can read every word first.
- **Your invite code** stays on your computer. It isn't shown, logged or put in
  reports.
- **Vendor sign-ins** happen in the vendor's own window. The Bridge doesn't read or
  store your vendor details.

<!-- The Bridge window shows the next section's text in-app (crates/view-model/src/locations.rs).
Keep its heading and wording exact, and keep it before any following "## " heading. -->

## Private files in older setups

Older setups now use the same private home as new setups. Windows programs can
no longer see your personal files through your account's home folder. Nothing
was deleted, moved or rewritten in your real home.

If a plug-in or vendor app asks you to sign in or activate again, open the vendor
app from Setup and re-activate once. Your licence is unaffected.

Advanced recovery, if re-activation is not possible: vendor data may previously
have been saved under ~/.config, ~/.local/share or ~/Documents. With the DAW and
vendor apps closed, copy only the specific vendor folder you need, on this same
machine, into the matching relative folder under the setup's private home:
~/.local/share/linux-vst-bridge/managed/environments/<setup-id>/home/
For example, ~/.config/VendorName becomes
~/.local/share/linux-vst-bridge/managed/environments/<setup-id>/home/.config/VendorName.
Choose the affected setup's ID; each setup has its own home. Keep the original
folder and avoid overwriting existing setup files. If you cannot identify the
right folder or setup, ask for help through your invitation contact. Never copy
licence or activation files between machines.

