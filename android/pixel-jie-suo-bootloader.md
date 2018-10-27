---
description: Pixel解锁Bootloader
---

# Pixel解锁Bootloader

## Pixel解锁Bootloader

1. Remove Google account and any kind of screen lock \(fingerprint, PIN, pattern, etc.\) from your device.
2. Eject sim card from your device.
3. Reset your device. In setup wizard, skip everything, don't connect to WiFi, don't add fingerprint or any kind of screen lock.
4. Go to Developer Options and enable USB debugging.
5. Connect your phone to PC.
6. Open CMD in adb directory and type

   ```text
   adb shell pm uninstall --user 0 com.android.phone
   ```

7. Restart your device.
8. Connect to WiFi, open Chrome and go to google.com \(or any website really\).
9. Go to Developer Options and enable OEM unlocking.
10. Reboot into bootloader and via CMD run

    ```text
    fastboot oem unlock
    ```

    or

    ```text
    fastboot flashing unlock
    ```

11. Profit

Be aware that unlocking bootloader removes everything from your device.

## Refs

[\[How-to\] Unlock bootloader on Verizon Pixel/XL](https://forum.xda-developers.com/pixel-xl/how-to/how-to-unlock-bootloader-verizon-pixel-t3796030)

