# GPG for GitHub and Gitea
## Generate new master GPG key
https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key

```shell
gpg --full-generate-key
```
- Go through the steps, just pick defaults
- Enter matching git name and email as the ones found in [gitconfig](git-config-scope.md)

## Generate new GPG subkey

Followed some of the steps from https://security.stackexchange.com/a/104241
```
gpg --expert --edit-key your_email@example.com
```

```
addkey
```

Follow prompts

```
save
```

```
gpg --export-secret-subkeys SUBKEYID
```

From `man gpg`, in reference to `--export-secret-subkeys`
> The second form of the command has the special property to render the secret part of the primary key useless; this is a GNU extension to OpenPGP and other implementations can not be expected to successfully import such a key.  Its intended use is in generating a full key with an additional signing subkey on a dedicated machine.  This command then exports the key without the primary key to the main machine.

So after this command, the original primary key's secret will not work. This explains why when I tried to add it to GitHub using the next section's steps, it did not work. What worked was following the next section's steps using the subkey that I imported onto my new machine.

## Adding a new GPG key to your GitHub or Gitea acount
Compare with [Adding a new SSH key to your GitHub or Gitea account](ssh-for-github-and-gitea.md#Adding%20a%20new%20SSH%20key%20to%20your%20GitHub%20or%20Gitea%20account).

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

Paste into Gitea and [GitHub](https://github.com/settings/keys) GPG keys section.

For Gitea's verification, had to first run this on Termux[^1].
It's also recommended to always add this to your `~/.bashrc`[^2].
```bash
export GPG_TTY=$(tty)
```


## Termux
When generating a GPG key in Termux, it may fail to verify in the source forge. When that happens, generate it on another device, then export it.[^3]
```shell
gpg --armor --export 3AA5C34371567BD2 > pub.asc
gpg --armor --export-secret-keys 3AA5C34371567BD2 > secret.asc
```

Transfer it to the Android device.
```
adb push pub.asc /sdcard/
adb push secret.asc /sdcard/
```

In Termux:
```shell
gpg --import pub.asc
gpg --import secret.asc
gpg --edit-key 3AA5C34371567BD2
gpg> trust
rm pub.asc secret.asc
```

## Cache password
[cache-gpg-key-password](cache-gpg-key-password.md)

## Next
[Sign Git Commits with GPG or SSH](sign-git-commits-with-gpg-or-ssh.md#Sign%20Git%20Commits%20with%20GPG%20or%20SSH)

[^1]: https://stackoverflow.com/a/57591830
[^2]: https://linux.die.net/man/1/gpg-agent
[^3]: https://gist.github.com/angela-d/8b27670bac26e4bf7c431715fef5cc51
