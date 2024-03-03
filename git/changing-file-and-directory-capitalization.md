
# Changing File and Directory Capitalization

The comment from https://stackoverflow.com/questions/10523849/how-do-you-change-the-capitalization-of-filenames-in-git works. Moving to an intermediate file/directory was key.
`git mv myfile foo; git mv foo MyFile`

Setting `core.ignorecase` did not work.

## Background

I found out the link to [custom-subdomain-for-github-pages](../DNS/custom-subdomain-for-github-pages.md) was broken on GitHub and Jekyll. Turned out after I renamed the folder in Obsidian, the change was not picked up by git. So, while all of my links used `DNS`, the folder in git was still `dns`.

Reference to broken README: https://github.com/lydavid/til/blob/ee167a2052ad63ac46e44aead0e080004d5de2db/README.md

Clicking the page leads to https://github.com/lydavid/til/blob/ee167a2052ad63ac46e44aead0e080004d5de2db/DNS/custom-subdomain-for-github-pages.md which is not found. Manually navigating to it shows that it indeed uses the lowercase form: https://github.com/lydavid/til/blob/ee167a2052ad63ac46e44aead0e080004d5de2db/dns/custom-subdomain-for-github-pages.md.