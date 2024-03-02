# Record Android Screen with ADB
I use this to record demos. Before I knew about this, I used Mac's `Cmd + Shift + 5`.

https://developer.android.com/tools/adb#screenrecord
```
adb shell screenrecord /sdcard/file.mp4
adb pull /sdcard/file.mp4 .
```
- Ctrl + C to stop
- adb supports tab completion for files on Android device
