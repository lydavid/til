# Record Android Screen with ADB
I use this to record demos. Before I knew about this, I used Mac's `Cmd + Shift + 5`.

https://developer.android.com/tools/adb#screenrecord
```
adb shell screenrecord /sdcard/video.mp4
adb pull /sdcard/file.mp4 .
```
- Ctrl + C to stop
- adb supports tab completion for files on Android device

If I run it in the background, I can get its process id like this to kill it.
```
adb shell screenrecord /sdcard/video.mp4 &
pid=$!
...
kill $pid
```
This worked on MacOS, but not in GitHub Actions, as seen in this [commit](https://github.com/lydavid/MusicSearch/pull/826/commits/0c5f19c2ca34bc666800572fd136558f442c7179) and [run](https://github.com/lydavid/MusicSearch/actions/runs/8494846929). I wonder if it's because of `/usr/bin/sh -c`. It was run in a `script` block of [android-emulator-runner](https://github.com/ReactiveCircus/android-emulator-runner). I ended up using [Maestro's startRecording](https://maestro.mobile.dev/api-reference/commands/startrecording) instead.