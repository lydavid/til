# Nested tmux

In order to use nested tmux sessions, I change my prefix key to `Ctrl` + `a` for my top-level terminals such as Termux.

[customize-tmux](customize-tmux.md):
```
set-option -g prefix C-a
```

Then for servers that I ssh into, I leave its prefix key as the default `Ctrl` + `b`.

I find this makes intuitive sense, as `C-a` controls the bottom-most session, then `C-b` controls the one above it. If there were a server that I would commonly ssh into from my `C-b` session, I would use `C-c`.