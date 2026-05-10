# RemoteX Desktop — releases

Signed macOS DMGs and the `latest-mac.yml` auto-update feed for [RemoteX Desktop](https://remotex.dev) — an AI-powered SSH command center for Mac.

**Source code lives on Bitbucket** (private). This repository only hosts release artifacts consumed by [`electron-updater`](https://www.electron.build/auto-update).

## Install

Grab the latest DMG from the [Releases](../../releases) page, or hit the marketing site:

```
https://remotex.dev/api/download?platform=mac
```

The download endpoint redirects to the latest signed DMG here. Apple Silicon and Intel builds are both available.

## What's in each release

| File | Purpose |
|---|---|
| `RemoteX-arm64.dmg` | Apple Silicon disk image |
| `RemoteX.dmg` | Intel disk image |
| `latest-mac.yml` | Auto-update feed read by the running app |
| `*.blockmap` | Differential update support for `electron-updater` |

## Verify the build

Every release is signed with an Apple Developer ID and notarized by Apple. To verify before installing:

```sh
# Verify the DMG is signed and notarized:
spctl -a -vvv -t install /path/to/RemoteX.dmg

# After installing, verify the .app:
codesign -dv --verbose=4 /Applications/RemoteX.app
```

A correctly notarized build prints `source=Notarized Developer ID` and shows a valid `Developer ID Application: <Your Name> (TEAMID)` identity.

## Auto-update

RemoteX checks this repo for new releases on launch and roughly once an hour while running. Updates download in the background and install on next launch. You can disable or change the update channel under **Settings → Updates** in the app.

## Issues and feedback

This repo is a release-artifact channel — it doesn't have Issues enabled. Please report bugs and request features at <https://remotex.dev/contact> or via the in-app feedback flow under **Settings → About**.

## License

Binaries published here are governed by the [RemoteX Terms of Use](https://remotex.dev/terms) that ship with the app. The repository itself is not separately open-source-licensed.
