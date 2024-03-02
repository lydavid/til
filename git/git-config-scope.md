# gitconfig vs git/config
From lowest to highest priority[^1]:

| scope       | file             | flag       |
| ----------- | ---------------- | ---------- |
| system wide | `/etc/gitconfig` | `--system` |
| user        | `~/.gitconfig`   | `--global` |
| repository  | `.git/config`    |            |

There's actually [more scopes](https://git-scm.com/docs/git-config#SCOPES), but I never explicitly configure these.

The default instructions I followed to set up [git-lfs](git-lfs.md) set up some system configs.
```
[filter "lfs"]
        smudge = git-lfs smudge -- %f
        process = git-lfs filter-process
        required = true
        clean = git-lfs clean -- %f
```

Windows Git Bash also added some configs.

On Windows Git Bash, I use `~/.gitconfig` for GitHub, and `.git/config` for my Obsidian notes which talks to Gitea.
By doing this, I can have a different `user.signingKey`, `user.name`, `user.email` to [sign commits](sign-git-commits-with-gpg-or-ssh.md) for each platform.


[^1]: https://stackoverflow.com/a/26824247
