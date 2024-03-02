# SSH for GitHub and Gitea
I use SSH for authentication. I prefer [gpg](gpg-for-github-and-gitea.md) for [signing commits](sign-git-commits-with-gpg-or-ssh.md).

## Generating a new SSH key
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Since I use multiple SSH keys, make sure to give them a descriptive name rather than leaving it as the default `id_ed25519`.


## Cache key password
[cache-ssh-key-password](cache-ssh-key-password.md)

## Adding a new SSH key to your GitHub or Gitea account

```shell
cat ~/.ssh/id_ed25519.pub
```
Copy its content.

When generating an SSH key on [Termux](Termux.md), it's easier to open Android Studio, browse the connected device (could be over WiFi), and copy the contents of this file under `/data/data/com.termux/files/home/.ssh/id_ed25519.pub`. Or simply double click it to open in AS, then copy its content.

Go to http://10.0.0.220:3000/user/settings/keys
Add Key
Paste the public key

In retrospect, I could have also just cat its content, and paste it into the browser on my phone.