# Shizuku — Core Scorpion build

Build of [thedjchi/Shizuku](https://github.com/thedjchi/Shizuku) (itself a fork of
[RikkaApps/Shizuku](https://github.com/RikkaApps/Shizuku)), Apache License 2.0, used by Ludex.

Kept from thedjchi: start on boot without root (waits for Wi-Fi), watchdog restart,
authenticated start/stop intents, Android 16/17 support.

Changed for Ludex:
- TCP mode (`adb tcpip`) is **off** by default: adb does not listen on the local network.
- The built-in updater is **off** by default and, if turned on, reads only
  `core-scorpion/Shizuku` releases. Ludex installs and updates this build itself, checking the
  APK signature and its SHA-256.
- Stealth mode is hidden: it renames the package and apps using Shizuku would lose it.
- Release builds refuse to fall back to the debug key: `signing.properties` (never committed)
  must point to the Core Scorpion keystore.
- Version names end in `-corescorpion`.

The package name stays `moe.shizuku.privileged.api`, so every app using the Shizuku API works.
Because the signature differs from the official app, switching from another Shizuku build needs
an uninstall first (and apps must be allowed again once).
