# Known issues — Pro Audio Bridge closed beta

Problems we already know about. You don't need to report these again, unless you
see something different. Numbers such as (#370) are our own tracking references;
you don't need to look them up. This list is updated for each release.

## Seen in 0.9.0-beta.1

- A report from a Steam Deck loses the word "Deck" from your description: the privacy
  filter removes your account's name, which on a Steam Deck is `deck`.
- If a report fails and then succeeds, the first failure's notice can stay at the
  bottom of the window. The report was sent if the window says "Sent".

## Not checked yet

- `0.9.0-beta.1` was checked on a clean Steam Deck with Bitwig and the free TyrellN6. It
  hasn't been tried on CachyOS yet (the same installer file), with REAPER, or with a
  paid plug-in that needs activation.
- Fedora and Ubuntu have no installer yet. Nothing has been checked on them.
- On CachyOS, nobody has heard a plug-in live yet: the test machine has no speakers.
- REAPER on SteamOS and Bitwig on CachyOS haven't been checked.
- Updating from the app through the public feed comes with the next release; it has
  been seen with a test feed on the Steam Deck.
- Restarting a stopped plug-in was seen working only with Serum 2 and TyrellN6 in
  Bitwig on the Steam Deck. Not tried in REAPER, or with other plug-ins playing in the same project.
- Opening the installer by double-clicking it hasn't been checked.
- Automation hasn't been tried.
- Kontakt's mapped MIDI controllers (mod wheel, pitch bend) haven't been confirmed (#410).
- Kontakt hasn't been checked after a reboot.
- Sound after a Bridge update hasn't been checked on the Steam Deck.
- No plug-in that needs iLok (PACE) has been tried (#414).
- Valhalla and CHOW plug-ins haven't been re-checked on current builds (#358, #359).
- The uninstall steps haven't been checked by reinstalling afterwards.

## Installing and setting up

- A file left by an earlier Bridge install can stop a fresh install, and the message
  doesn't name the file. Do every uninstall step in the guide before installing again.
- An installer stopped by the 1-hour limit is reported as "The installation finished,
  but no instruments or effects were found".
- The status says "Bridge service status unavailable" while the Windows runtime
  downloads. Wait for the download to finish.
- Some refusals show a code instead of words, such as "This request was refused:
  no_supported_instruments_or_effects_discovered". Send us a report with the code.
- After a setup check fails, its card can show a code such as
  unchanged_publication_configuration_changed.
- After another installer runs in a setup, its plug-ins briefly say "needs attention",
  "Plug-in controls could not be loaded" or "DAW connection needs attention". This
  clears by itself.
- "The selected installer is unavailable in this readback" can show on Setup after an
  installer runs in another setup, until the page refreshes.
- A setup marked "A different setup is already available" keeps saying so after the
  other copy is removed from the DAW, and Continue doesn't check it again.
- A new setup can say a plug-in's connection "could not be placed" when another setup
  already provides that plug-in.
- A plug-in connected through a licence manager's setup is listed under that setup's
  name, such as "… · License Support Win64".
- The Native Access setup says "Open it below", but there is no button there. Open a
  plug-in it installed and use **Add plug-ins through Native Access**.
- After an update, a setup can say it needs attention while its plug-ins are available.

## Activating

- A sign-in page opened by an app or plug-in appears behind the window that asked for
  it. Look for it in the taskbar.
- Right after you sign in, Native Access may say it couldn't load your products. Its
  first scans are slow. Wait, then try again in Native Access.

## The Bridge window

- The new window has only been seen on the Steam Deck. Setup, Activity, Diagnostics
  and Send a report aren't all at their final layout yet.
- On larger screens the window doesn't scale up yet.
- Screen readers can't see the window's buttons.
- "Fix it step by step" is offered first even on a plug-in that is fully working.
  You can ignore it.
- Searching plug-ins doesn't match the setup name shown in the row.
- Failure text in a plug-in's "Is it ready?" row is cut off at the right edge.
- In REAPER, "Restarting processing" turns green when a plug-in loads. REAPER does
  this itself; it's normal.
- A report can list "Historical qualified DAW: Bitwig Studio 6.1 Flatpak" on a REAPER
  machine, with its DAW fields empty. Name your DAW in your description.

## Updating

- An older installer's Setup window offers "Update Bridge" and really takes you back a
  version. Plug-ins kept working when this was seen, but don't do it.
- **Restore previous setup** is only reachable by opening an installer file again. The
  window has no button for it.
- A refused update shows only a code on Setup, such as
  preset_configured_drive_not_qualified. Send us a report with it.
- An update was refused once on a test build, and its message wasn't kept, so the cause
  is unknown. If it happens to you, send a report.
- Once, after a failed update, plug-ins wouldn't load while the window still said they
  were ready. Not yet understood.
- The **View update** link can wrap one letter per line after an update.
- The update's progress shows a box character before "Installing application files".

## In your DAW

- Bitwig's device panel can show a plug-in's internal ID, such as "LVB_5653…", instead
  of its name.
- A plug-in with no window of its own may still be offered an editor, which opens
  empty (#472). Use your DAW's own controls for it.
- Windows plug-in windows aren't scaled up on high-resolution screens (#407).
- Now and then a key press is lost after clicking back into a plug-in's window, under
  heavy load (#598).
- On the Steam Deck, the taskbar's system tray can flicker while some vendor apps run
  (#546).
- Uninstalling doesn't remove Flatpak Bitwig's Bridge permission by itself (#370). The
  guide's uninstall steps show the one command.
- Sample folders can be added, and they survive a reboot and an update. No plug-in has
  been seen reading samples through one yet.

## Plug-ins

- **Serum 2:** some editor areas look too bright or see-through: the oscillator,
  envelope, LFO and filter fills (#330). Sound, controls and saved state are not
  affected.
- **Valhalla Freq Echo:** was silent at a 256-sample buffer on an earlier build (#399).
  Use a 512-sample buffer in your DAW if you hear silence.
- **Guitar Rig:** says "native DAW connection could not be prepared" and doesn't connect
  yet (#595). No workaround.
- **Blackhole and BEAM:** their editor windows don't draw properly (#132).
