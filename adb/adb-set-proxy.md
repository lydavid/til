# ADB Set Proxy
Recently I learned[^1] adb allows setting and unsetting proxy.

Very useful for Charles. After setting up Charles root certificate, and running Charles, I can just toggle it on/off.

```
adb shell settings put global http_proxy 192.168.1.13:8888
```
- This IP/port is the IP of the host running Charles, and Charles' port

```
adb shell settings put global http_proxy :0
```

Note that these do not change the values of the `Proxy hostname` and `Proxy port` set in `AndroidWifi` (emulator's default wifi), but seems to take precedence. It's not necessary to even set it in the UI.

[^1]: https://www.youtube.com/watch?v=xp8ufidc514&t=490s