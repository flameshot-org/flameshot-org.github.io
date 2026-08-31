+++
title = "Install on macOS"
description = "Flameshot is a powerful yet simple to use screenshot software."
date = 2021-05-01T08:00:00+00:00
updated = 2024-05-30T08:00:00+00:00
draft = false
weight = 2
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'How to install Flameshot on macOS.'
toc = true
top = true
+++

## Installation on macOS (OSXI)

You can install Flameshot on [macOS](https://en.wikipedia.org/wiki/MacOS) using the either of the following:

- [MacPorts](https://ports.macports.org/port/flameshot/summary): `sudo port selfupdate && sudo port install flameshot`
- [Homebrew](https://formulae.brew.sh/cask/flameshot): `brew install --cask flameshot`
    > Note that because of macOS security features, you may not be able to open flameshot when installed using brew. If you see the message `“flameshot” cannot be opened because the developer cannot be verified.` you will need to follow the steps below:
    >
    > 1. Go to the Applications folder (Finder > Go > Applications, or Shift+Command+A)
    > 2. Right-Click on `flameshot.app` and choose `Open` from the context menu
    > 3. In the dialog click `Open`
    > 4. Click `Done` - don't move to trash
    > 5. Go to Settings > Privacy & Security and scroll down until you see Flameshot was blocked, and click `Open Anyway`
    > 6. Next you'll see a dialog about Flameshot requesting permission to record the screen
    > 7. Open Settings again, an you should be looking at the Screen & System Audio Recording section under Privacy & Security, where a toggle needs to be set to `On` for Flameshot. Toggle it on.
    >
    > After following all those steps above, you should see the Flameshot icon in the menubar and Flameshot will open without problems on your Mac.
    >
    > **Note:** As of 2026-09-01, the Homebrew cask for Flameshot is disabled
    > (`fails_gatekeeper_check`) because the macOS build isn't notarized with a paid
    > Apple Developer ID. `brew install --cask flameshot` and `brew upgrade --cask flameshot`
    > will no longer work — your existing install keeps running, but Homebrew won't give you
    > further updates. See [Keeping Flameshot updated on macOS](#keeping-flameshot-updated-on-macos)
    > below for an alternative.
- Download DMG file:
    1. Navigate to [the release page on GitHub](https://github.com/flameshot-org/flameshot/releases)
    2. From the assets of the latest stable release, download the latest DMG file
    3. Double-click on the DMG file you downloaded
    4. Drag and drop the `flameshot.app` to your `/Applications` folder
    5. macOS restricts applications from accessing the screen. Therefore you have to give Flameshot security permissions to "record" your desktop.
        ![A picture of the macOS Security & Privacy settings that shows the Flameshot should be added to the list in the "privacy" tab](/media/macos_permissions.png)

## Keeping Flameshot updated on macOS

If you installed Flameshot via the DMG (or your Homebrew cask has stopped working — see the note
above), there's no package manager keeping your install current. The script below checks
[GitHub Releases](https://github.com/flameshot-org/flameshot/releases) for a newer version daily and
installs it automatically, verifying the download's checksum before touching anything.

> This is a community-contributed workaround, not an official updater. It won't be necessary once
> Flameshot ships notarized, Developer-ID-signed macOS builds — track progress in
> [#4125](https://github.com/flameshot-org/flameshot/issues/4125).

### How it works

1. Reads the installed version from `/Applications/Flameshot.app/Contents/Info.plist`.
2. Queries the GitHub Releases API for the latest tag.
3. If newer, downloads the `*-macos-arm64.dmg` asset (use `*-macos-intel.dmg` on Intel Macs).
4. Verifies the download against the `.sha256sum` file GitHub publishes alongside it — it aborts and
   does not install if the checksum doesn't match.
5. Mounts the `.dmg`, copies `Flameshot.app` into `/Applications`, and removes the
   `com.apple.quarantine` attribute (required since the build isn't notarized — otherwise Gatekeeper
   blocks the first launch).
6. Sends a macOS notification with the version change. It does not force-quit a running Flameshot —
   restart it manually to pick up the update.

Works identically for a first install: if Flameshot isn't present yet, the script treats that as
version `0` and installs the latest release the same way.

### 1. Install the script

Save as `~/Library/Application Support/com.user.flameshot-autoupdate/flameshot_autoupdate.sh` and make
it executable with `chmod +x`:

```bash
#!/bin/bash
set -euo pipefail

REPO="flameshot-org/flameshot"
APP_PATH="/Applications/Flameshot.app"
LOCK_FILE="/tmp/flameshot-autoupdate.lock"
WORKDIR=""
MOUNT_POINT=""

# On Intel Macs, change every "macos-arm64" below to "macos-intel"

log() {
  echo "[$(/bin/date '+%Y-%m-%d %H:%M:%S')] $*"
}

notify() {
  /usr/bin/osascript -e "display notification \"$2\" with title \"$1\"" >/dev/null 2>&1 || true
}

cleanup() {
  if [ -n "$MOUNT_POINT" ] && [ -d "$MOUNT_POINT" ]; then
    /usr/bin/hdiutil detach "$MOUNT_POINT" -quiet -force >/dev/null 2>&1 || true
  fi
  if [ -n "$WORKDIR" ] && [ -d "$WORKDIR" ]; then
    /bin/rm -rf "$WORKDIR"
  fi
  /bin/rm -f "$LOCK_FILE"
}
trap cleanup EXIT

if [ -e "$LOCK_FILE" ]; then
  log "Another run appears to be in progress ($LOCK_FILE exists) — skipping."
  exit 0
fi
touch "$LOCK_FILE"

CURRENT_VERSION="0"
if [ -f "$APP_PATH/Contents/Info.plist" ]; then
  CURRENT_VERSION=$(/usr/bin/defaults read "$APP_PATH/Contents/Info.plist" CFBundleShortVersionString 2>/dev/null || echo "0")
fi

LATEST_JSON=$(/usr/bin/curl -fsSL --max-time 30 "https://api.github.com/repos/$REPO/releases/latest") || {
  log "Failed to reach GitHub releases API."
  exit 1
}

LATEST_TAG=$(echo "$LATEST_JSON" | /usr/bin/python3 -c "import json,sys; print(json.load(sys.stdin)['tag_name'])")
LATEST_VERSION="${LATEST_TAG#v}"

DMG_URL=$(echo "$LATEST_JSON" | /usr/bin/python3 -c "
import json, sys
data = json.load(sys.stdin)
for asset in data['assets']:
    if asset['name'].endswith('macos-arm64.dmg'):
        print(asset['browser_download_url'])
        break
")

if [ -z "$DMG_URL" ]; then
  log "No macos-arm64.dmg asset found in release $LATEST_TAG — skipping."
  exit 0
fi

if [ "$CURRENT_VERSION" = "$LATEST_VERSION" ]; then
  log "Flameshot already at latest version ($CURRENT_VERSION)."
  exit 0
fi

log "New version available: $CURRENT_VERSION -> $LATEST_VERSION"

WORKDIR=$(/usr/bin/mktemp -d)
DMG_PATH="$WORKDIR/flameshot.dmg"
SHA_PATH="$WORKDIR/flameshot.dmg.sha256sum"

/usr/bin/curl -fsSL --max-time 300 "$DMG_URL" -o "$DMG_PATH"
/usr/bin/curl -fsSL --max-time 30 "${DMG_URL}.sha256sum" -o "$SHA_PATH"

EXPECTED_SHA=$(/usr/bin/awk '{print $1}' "$SHA_PATH")
ACTUAL_SHA=$(/usr/bin/shasum -a 256 "$DMG_PATH" | /usr/bin/awk '{print $1}')

if [ "$EXPECTED_SHA" != "$ACTUAL_SHA" ]; then
  log "Checksum mismatch for $LATEST_TAG! expected=$EXPECTED_SHA actual=$ACTUAL_SHA — aborting, not installing."
  notify "Flameshot update FAILED" "Checksum mismatch for v$LATEST_VERSION. Not installed — see log."
  exit 1
fi
log "Checksum verified for $LATEST_TAG."

MOUNT_POINT=$(/usr/bin/hdiutil attach "$DMG_PATH" -nobrowse -readonly | /usr/bin/tail -1 | /usr/bin/awk -F'\t' '{print $NF}')

SRC_APP=$(/usr/bin/find "$MOUNT_POINT" -maxdepth 1 -iname "Flameshot.app" | head -1)
if [ -z "$SRC_APP" ]; then
  log "Could not find Flameshot.app inside mounted dmg at $MOUNT_POINT."
  exit 1
fi

NEW_APP_TMP="/Applications/.Flameshot.app.new"
/bin/rm -rf "$NEW_APP_TMP"
/bin/cp -R "$SRC_APP" "$NEW_APP_TMP"

/usr/bin/hdiutil detach "$MOUNT_POINT" -quiet
MOUNT_POINT=""

/usr/bin/xattr -dr com.apple.quarantine "$NEW_APP_TMP" 2>/dev/null || true

/bin/rm -rf "$APP_PATH"
/bin/mv "$NEW_APP_TMP" "$APP_PATH"

log "Installed Flameshot $LATEST_VERSION to $APP_PATH."
notify "Flameshot updated" "Updated $CURRENT_VERSION -> $LATEST_VERSION (checksum verified). Restart Flameshot to use it."
```

### 2. Schedule it with launchd

Save as `~/Library/LaunchAgents/com.user.flameshot-autoupdate.plist`, replacing `YOUR_USERNAME` with
your own:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.user.flameshot-autoupdate</string>
  <key>Program</key>
  <string>/Users/YOUR_USERNAME/Library/Application Support/com.user.flameshot-autoupdate/flameshot_autoupdate.sh</string>
  <key>ProgramArguments</key>
  <array>
      <string>/Users/YOUR_USERNAME/Library/Application Support/com.user.flameshot-autoupdate/flameshot_autoupdate.sh</string>
  </array>
  <key>StandardErrorPath</key>
  <string>/Users/YOUR_USERNAME/Library/Logs/com.user.flameshot-autoupdate/com.user.flameshot-autoupdate.out</string>
  <key>StandardOutPath</key>
  <string>/Users/YOUR_USERNAME/Library/Logs/com.user.flameshot-autoupdate/com.user.flameshot-autoupdate.out</string>
  <key>StartCalendarInterval</key>
  <dict>
    <key>Hour</key>
    <integer>13</integer>
    <key>Minute</key>
    <integer>15</integer>
  </dict>
  <key>LowPriorityBackgroundIO</key>
  <true/>
  <key>LowPriorityIO</key>
  <true/>
  <key>ProcessType</key>
  <string>Background</string>
</dict>
</plist>
```

Then load it:

```bash
chmod +x "$HOME/Library/Application Support/com.user.flameshot-autoupdate/flameshot_autoupdate.sh"
plutil -lint "$HOME/Library/LaunchAgents/com.user.flameshot-autoupdate.plist"
launchctl load -w "$HOME/Library/LaunchAgents/com.user.flameshot-autoupdate.plist"
```

This runs the check daily at 1:15pm local time — adjust `Hour`/`Minute` as needed. Check its status
with `launchctl list | grep flameshot-autoupdate`; disable it with
`launchctl unload ~/Library/LaunchAgents/com.user.flameshot-autoupdate.plist`.

### Security notes

- This removes Gatekeeper's quarantine flag from the downloaded app, which is only reasonable because
  the script verifies the download against GitHub's published SHA-256 checksum first. That confirms the
  download matches what's on the release page — it does not verify a cryptographic signature, since the
  build isn't signed with a Developer ID. Only use this against a release repo you trust.
- If the checksum doesn't match, the script aborts, notifies you, and does not install anything.
