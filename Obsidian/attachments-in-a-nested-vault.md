
# Attachments in a Nested Vault


The directory structure of my root Obsidian vault looks something like this (edited from `tree .`).

```
.
├── attachments (stored in git lfs in Gitea)
│   └── image.jpg
├── Personal (stored in git in Gitea)
├── til
│   ├── Obsidian (stored in git in GitHub)
│   └── attachments (stored in git lfs in GitHub)
│       └── otherimage.png
```

I usually have a single vault opened at the root. This lets me edit my personal notes, as well as the public-facing notes under the `til` directory.

Linking between notes is as simple as typing `[[`[^1], then filtering for the page I wish to link to. Linking between the root and sub vault will always be visible to me when browsing Obsidian. However, some of the links in the sub vault that links to the root vault will be broken when viewed on GitHub or Jekyll.

When I drag and drop an image into the Obsidian editor, it will put the image under `attachments` and create a relative link to it. When I want an image to be visible on GitHub (and stored in its [git lfs](../git/git-lfs.md)), I need to `Open another vault` with Obsidian. Then I can drag and drop, and it will end up under `til/attachments`.




[^1]: https://help.obsidian.md/Linking+notes+and+files/Internal+links#Link+to+a+file