# Connect ADB Wirelessly on the Same Network

https://github.com/Genymobile/scrcpy/blob/master/doc/connection.md#tcpip-wireless
```
adb connect 192.168.1.2
```
- On the device, accept the popup dialog

If it refuses, then plug it into my computer and run
```
scrcpy --tcpip
```
This will open port 5555. Then disconnect the device, and reconnect using its IP.

Now I can interact with it through adb, scrcpy, or Android Studio.

This extends to Google/Android TVs. It's great for sideloading apps unto it.

## Disconnect without `kill-server`
```
adb disconnect 192.168.1.21
```

```
adb disconnect
```
