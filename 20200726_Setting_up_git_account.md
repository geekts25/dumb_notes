#  20200726  Setting up git account

## Generate ssh key

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/geekts/.ssh/id_rsa): geekts
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in geekts.
Your public key has been saved in geekts.pub.
# set permission for key
$ chmod 600 ~/.ssh/geekts
$ chmod 600 ~/.ssh/geekts.pub
```

## Add public key to github

Register geekts.pub to GitHub.

https://docs.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account

Test SSH Connection

```
$ ssh -v -T git@github.com -i ~/.ssh/geekts
...
Hi geekts25! You've successfully authenticated, but GitHub does not provide shell access.
```

## Setup ssh config for github

Open or create ~/.ssh/config. Add fellowing code to it.

```
# ~/.ssh/config
host geekts25.github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/geekts
 PreferredAuthenticationsi publickey
```

## Clone git repo and try pushing

```
$ cd ~/git_projs
$ git clone https://github.com/geekts25/dumb_notes.git
$ cd dump_notes
$ git push origin HEAD
```

