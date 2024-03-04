# GPG for GitHub and Gitea
## Generate new GPG key
https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key

```shell
gpg --full-generate-key
```
- Go through the steps, just pick defaults
- Enter matching git name and email as the ones found in [gitconfig](git-config-scope.md)

List all keys
```shell
gpg --list-secret-keys --keyid-format=long
```

```shell
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
```

Copy the GPG key ID after the `/`
```shell
gpg --armor --export 3AA5C34371567BD2
```

Paste into [Gitea](Gitea.md) and [GitHub](https://github.com/settings/keys) GPG keys section.

For Gitea's verification, had to first run this on Termux[^1].
It's also recommended to always add this to your `~/.bashrc`[^2].
```bash
export GPG_TTY=$(tty)
```

## Cache password
[cache-gpg-key-password](cache-gpg-key-password.md)

## Next
[Sign Git Commits with GPG or SSH](sign-git-commits-with-gpg-or-ssh.md#Sign%20Git%20Commits%20with%20GPG%20or%20SSH)

[^1]: https://stackoverflow.com/a/57591830
[^2]: https://linux.die.net/man/1/gpg-agent

