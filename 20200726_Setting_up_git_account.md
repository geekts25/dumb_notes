#  20200726  Setting up git account

## Generate ssh key

```bash
$ ssh-keygen -t rsa -C "geekts-mac"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/geekts/.ssh/id_rsa): geekts
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in geekts.
Your public key has been saved in geekts.pub.
# set permission for key
$ chmod 600 ~/.ssh/geekts
$ chmod 600 ~/.ssh/geekts.pub
# add key to ssh
$ ssh-add ~/.ssh/geekts
Identity added
```

## Add public key to github

Register geekts.pub to GitHub.

https://docs.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account

Test SSH Connection

```bash
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

## Config git

```bash
$ git config --global user.name "geekts"
$ git config --global user.email "geekts25@gmail.com"
# check config works
$ git config --list | grep user
user.name=geekts25
user.email=geekts25@gmail.com
```

## Clone git repo and try pushing

```bash
$ cd ~/git_projs
$ git clone https://github.com/geekts25/dumb_notes.git
$ cd dump_notes
$ touch README.mk
$ git commit -a -m "initial commit"
$ git remote add origin git@github.com:geekts25/dumb_notes.git
# git : User
# github.com : HostName
$ git push origin HEAD
```

