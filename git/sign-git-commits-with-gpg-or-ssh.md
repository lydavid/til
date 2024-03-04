# Sign Git Commits with GPG or SSH

## With GPG
Pre: [GPG for GitHub and Gitea](gpg-for-github-and-gitea.md#GPG%20for%20GitHub%20and%20Gitea)

https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key#telling-git-about-your-gpg-key

```shell
git config --unset gpg.format
```

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
git config user.signingkey 3AA5C34371567BD2
```

```shell
git config commit.gpgsign true
```

## With SSH
Pre: [SSH for GitHub and Gitea](ssh-for-github-and-gitea.md#SSH%20for%20GitHub%20and%20Gitea)

https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key#telling-git-about-your-ssh-key

```bash
git config gpg.format ssh
```

```bash
git config user.signingkey ~/.ssh/id_ed25519.pub
```

https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits
```bash
git config commit.gpgsign true
```

