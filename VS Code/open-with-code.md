
# Open with Code

Turned out I didn't have "Open with Code" set up this entire time. I had to right-click within a folder, "Open in Git Bash here", then `code .`.

## Setup

To get "Open with Code", I had to reinstall[^1], and make sure to check the following:

![](../attachments/Screenshot%202024-03-02%20213447.jpg)

The default terminal was PowerShell. I switched it to WSL with `Select Default Profile`[^2].

## WSL

This runs on my Windows host. But VS Code allows me to connect to it as a remote window. When connected this way, everything I do in VS Code will execute in the WSL environment[^3].

![](../attachments/Screenshot%202024-03-02%20215136.jpg)

After opening a folder for the first time, I left-click VS Code on my taskbar, drag up, and select what I'm looking for from the Recent Folders.

![](../attachments/Screenshot%202024-03-02%20213230.jpg)


[^1]: https://github.com/Microsoft/vscode/issues/63714
[^2]: https://stackoverflow.com/a/67501013
[^3]: https://code.visualstudio.com/docs/remote/wsl#_open-a-remote-folder-or-workspace