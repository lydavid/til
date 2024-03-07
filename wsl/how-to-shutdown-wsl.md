# How to Shutdown WSL
This immediately terminates all running distributions[^1].
```
wsl --shutdown
```

Just exiting all wsl sessions is not enough. Notice how Vmmem still takes up resources in Task Manager.

[^1]: https://learn.microsoft.com/en-us/windows/wsl/basic-commands#shutdown