
# ADB Shell to Execute Commands

## One-off
```shell
adb shell input text "hello world"
```

Also useful for typing out long commands with my keyboard to be executed in Termux.
```shell
adb shell input text "'git config user.email \"22302001+lydavid@users.noreply.github.com\"'"
```
- Escape double-quotes with backslashes, and make sure to wrap with `"' '"`

## Enter shell
```shell
adb shell
panther:/ $ input text "hello world"
```
