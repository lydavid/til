
# Manage dotfiles with stow
In WSL and Ubuntu Server, the default `.bashrc` includes this:
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

So, I moved some of my aliases out into `.bash_aliases`.

I decided to put this in a public [repository](https://github.com/lydavid/dotfiles) so that I can access these from anywhere, without necessarily signing into GitHub.

With stow, replicating my dotfiles across all my devices/users is as simple as `git clone https://github.com/lydavid/dotfiles` into the home directory, then `stow .` from the dotfile repository[^1].

For some of my users, their home directory is a git repository. They should `git add submodule https://github.com/lydavid/dotfiles` instead, so that they don't redundantly commit the dotfiles repository.

[^1]: https://www.youtube.com/watch?v=y6XCebnB9gs