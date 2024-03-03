# TIL

> Today I Learned

A collection of concise write-ups on small things I learn day to day across a
variety of languages and technologies. These are things that don't really
warrant a full blog post.


_16 TILs and counting..._

---

### Categories

* [Android-Studio](#Android-Studio)
* [DNS](#DNS)
* [Kotlin](#Kotlin)
* [adb](#adb)
* [git](#git)

---

### Android-Studio

- [Multipreview](Android-Studio/jetpack-compose-multipreview.md)

### DNS

- [Setting up Custom Subdomain for GitHub Pages](DNS/custom-subdomain-for-github-pages.md)

### Kotlin

- [Generic Invariance](Kotlin/generic-invariance.md)

### adb

- [ADB Set Proxy](adb/adb-set-proxy.md)
- [Connect ADB Wirelessly on the Same Network](adb/connect-adb-wirelessly.md)
- [Record Android Screen with ADB](adb/record-android-screen-with-adb.md)

### git

- [Cache GPG key password](git/cache-gpg-key-password.md)
- [Cache SSH key password](git/cache-ssh-key-password.md)
- [GPG for GitHub and Gitea](git/gpg-for-github-and-gitea.md)
- [Git Large File Storage](git/git-lfs.md)
- [Git Submodules with Different Remote Hosts](git/git-submodules-with-different-remote-hosts.md)
- [Run GitHub Actions from Command Line with gh](git/run-gha-from-cli-with-gh.md)
- [SSH for GitHub and Gitea](git/ssh-for-github-and-gitea.md)
- [Sign Git Commits with GPG or SSH](git/sign-git-commits-with-gpg-or-ssh.md)
- [gh auth](git/gh-auth.md)
- [gitconfig vs git/config](git/git-config-scope.md)

## Usage

After creating a new entry, run `./createReadme.py > README.md` to regenerate
the readme with the new data.

If you are using git, you can install this script as a pre-commit git hook so
that it is autogenerated on each commit.  Use the following command:
    cd .git/hooks/ && ln -s ../../createReadme.py pre-commit && cd -


## About

I shamelessly stole this idea from
[jbranchaud/til](https://github.com/jbranchaud/til) who claims to have stolen
it from others.

## Other TIL Collections

* [jbranchaud/til](https://github.com/jbranchaud/til) who claims to have stolen
* [Today I Learned by Hashrocket](https://til.hashrocket.com)
* [jwworth/til](https://github.com/jwworth/til)
* [thoughtbot/til](https://github.com/thoughtbot/til)

## License

&copy; 2017-2018 Jim Anderson

This repository is licensed under the MIT license. See `LICENSE` for
details.