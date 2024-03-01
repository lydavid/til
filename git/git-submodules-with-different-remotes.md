
This is a public repository on GitHub that is being used as a [submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) of my private personal repository on Gitea.

If I run this from `Obsidian` and from `Obsidian/til`, the see the following results.
```
git config --list | rg remote
```

```
remote.origin.url=https://github.com/lydavid/til.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
```

```
remote.origin.url=git@10.0.0.2:lydavid/Obsidian.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.obsidian.remote=origin
```
