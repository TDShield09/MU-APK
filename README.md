# MU Android update storage

This branch is storage for the Android APK's updater. Update logic stays in the Android app source.

## Files and APK updates

- `SPK.txt` is checked by the app before the game starts.
- Each game file row keeps its full path relative to the writable game root, followed by CRC32, byte size, and HTTPS URL: `path;CRC32;size;URL`.
- Android payload files are stored under `mobile-payload/` with the same game-root-relative paths. For example, `Data/Custom/VIPCharRank.txt` maps to `mobile-payload/Data/Custom/VIPCharRank.txt`.
- `apk/name.apk` rows point to APK assets uploaded to GitHub Releases. The app downloads and verifies the APK, then asks Android's package installer to apply it. The replacement must have a higher version code and the same signing certificate as the installed APK.

Publish patch files and the APK asset before updating `SPK.txt`. Keep large APKs and game binaries out of Git; GitHub Release assets hold those files.
