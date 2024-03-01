
This is a public repository on GitHub that is being used as a [submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) of my private personal repository on Gitea.

If I run the following from `Obsidian` and from `Obsidian/til`
```
git config --list | rg remote
```

I see the following results
```
remote.origin.url=git@github.com:lydavid/til.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
```

```
remote.origin.url=git@10.0.0.2:lydavid/Obsidian.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.obsidian.remote=origin
```

One of the issues I encountered while setting this up was I had `commit.gpgsign` set up globally. So I had to disable it.
```
git config --global --unset commit.gpgsign
```

Then set it up locally for the root git repository. I did not set it up for this repository yet because it uses a different email.
