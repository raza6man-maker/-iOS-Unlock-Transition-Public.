# iOS Unlock Transition

Native Kotlin app (Android 13+, tested target: Redmi 15, Android 16 / HyperOS 3).
No root, no ADB, no special permissions, no services running in the background.

## Install (phone only, no computer)
1. Create a free GitHub account, make a new repository, upload this folder's contents
   (GitHub website → Add file → Upload files; keep the `.github` folder).
2. Open the **Actions** tab → **Build APK** → **Run workflow**. Wait ~4 minutes.
3. Open the finished run → **Artifacts** → download `iOS-Unlock-Transition-apk` (a zip), extract it
   with the Files app, tap `app-release.apk`.
4. HyperOS asks to allow "Install unknown apps" for your browser/Files app. Allow it, then install.

Alternative with a computer: open the folder in Android Studio, let it sync, Build → Build APK(s).

## Use
- Open the app → **Preview animation** (safe, in-app).
- Optional: **Use as Home app** → choose "iOS Unlock Transition". After you unlock the phone, the
  home screen then zooms in and the icons scale 85%→100% with a staggered fade.
  To revert: Settings → Home screen → pick your original launcher.

## What works vs. what needs system privileges
| Feature | Status |
|---|---|
| Zoom-in + staggered icon scale/fade on this app's home screen | Works (normal app) |
| Replaying it after unlock | Works when set as Home app (detects screen-off, plays on next appearance) |
| Changing the system lock-screen unlock animation | Not possible: SystemUI, needs system/signature privileges |
| Animating the stock HyperOS launcher (POCO/Mi Home) icons | Not possible without a system theme/mod |
| Overlays on the lock screen / reading PIN or fingerprint | Intentionally not implemented |

## Notes
- HyperOS may restrict third-party launchers' autostart; if the home screen reloads slowly, allow
  "Autostart" and set Battery saver → "No restrictions" for this app (optional).
- Cost: one hardware layer for ~400 ms, ~24 view animations, no blur, no polling.
- Release APK is signed with the debug key so it installs directly; use your own key to publish.
