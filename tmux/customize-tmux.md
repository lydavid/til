
# Customize tmux
```
vi ~/.tmux.conf
```

## My current configurations
https://github.com/lydavid/dotfiles/blob/main/.tmux.conf

For [nested-tmux](nested-tmux.md), I need to comment out the top-level terminal preferences.

## Apply changes

From shell
```
tmux source ~/.tmux.conf
```

Or, from tmux command prompt[^1]
`<prefix key>`, `:`, `source ~/.tmux.conf`

[^1]: https://github.com/tmux/tmux/wiki/Getting-Started#the-configuration-file