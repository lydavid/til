
# Speed Up Git in WSL

I put `alias git=git.exe` in my `.bashrc`.[^1]

## Quirks
This seems to mess up ssh. Despite [adding my ssh key to the ssh-agent](../git/cache-ssh-key-password.md), it will keep prompting for a password. In order to pull, I have to use:
```
/usr/bin/git pull
```

`git config --global` are stored/sourced from `/mnt/c/Users/username/.gitconfig`. I'm used to being able to view my global configs with `vi ~/.gitconfig`. To fix this, I need to symlink from the Windows' user's home to WSL's home.
Insider WSL:
```
cd /mnt/c/Users/username
ln -s ~/.gitconfig .gitconfig
```

This doesn't play nicely with [stow](../bash/manage-dotfiles-with-stow.md), which is set up in WSL's home. It would be nice if my `.gitconfig ` in my dotfiles were automatically moved to Window's home, then symlinked to WSL's home. Right now, I have to do it manually. Symlinking from WSL's home to Window's home breaks `git.exe`.


[^1]: [https://gist.github.com/jasonboukheir/3fdab92ece236744528447a4f7f5de00?permalink_comment_id=4330152#gistcomment-4330152](https://gist.github.com/jasonboukheir/3fdab92ece236744528447a4f7f5de00?permalink_comment_id=4330152#gistcomment-4330152)