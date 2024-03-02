# ADB Set Proxy
Recently I learned[^1] adb allows setting and unsetting proxy.

Very useful for [Charles proxy](../../Reference/Network/Debugging/Charles/Charles%20proxy.md). After setting Charles root certificate up, and running Charles, I can just toggle it on/off.

```
adb shell settings put global http_proxy 192.168.1.13:8888
```
- This IP/port is the IP of the host running Charles, and Charles' port

```
adb shell settings put global http_proxy :0
```

Note that these do not change the values of the `Proxy hostname` and `Proxy port` set in `AndroidWifi` (emulator's default wifi), but seems to take precedence. So, I can leave them set in the UI, and just toggle proxy with the command line.

[^1]: https://www.youtube.com/watch?v=xp8ufidc514&t=490s