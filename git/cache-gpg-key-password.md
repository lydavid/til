# Cache GPG key password
Keywords: PGP, OpenPGP

For my Obsidian, I'm using [SSH](../../til/git/ssh-for-github-and-gitea.md) to push/pull, so I need to [Cache SSH key password](cache-ssh-key-password.md#Cache%20SSH%20key%20password) as well.

## One-time setup per user
Add these lines to `~/.gnupg/gpg-agent.conf`[^1]
```
default-cache-ttl 34560000
max-cache-ttl 34560000
```

## Run each time device restarts
```
gpgconf --kill gpg-agent
gpg-agent --daemon
```


[^1]: https://superuser.com/a/624488
