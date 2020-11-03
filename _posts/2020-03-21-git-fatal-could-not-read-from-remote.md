---
title: 'Git "fatal: Could not read from remote repository"'
last_modified_at: 2020-03-22
categories:
  - productivity
tags:
  - git
toc: true
classes: narrow
---

When you work with a remote repository it's not rare to bump into this error: 

    fatal: Could not read from remote repository
	
For example, when you push local commits to a remote branch you may get this error:

```
Pushing to git@github.com:<path to repo>
fatal: Could not read from remote repository.
Please make sure you have the correct access rights and the repository exists.
```

There are different reasons and solutions for this problem according to different scenarios. Check the situations below to see if your problem is listed.

## Working from a remote device

When you work from home and have ssh-ed to your company computer, you may bump into this error. If an SSH key is generated and used on the remote device (see [SSH agent passphrase](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/working-with-ssh-key-passphrases)), and the SSH key is passphrase-protected, you need to enter that passphrase in order to use the protected key (see [Adding your SSH key to the ssh-agent](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)). On the remote device run:

```
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/<private key file>
```

## Magit
### Using Magit on Emacs on Windows

If you are using Emacs and Magit on Windows, and your remote repository access is configured with an SSH passphrase, then you need to add the following configuration to Emacs (v26.3) to let it work with SSH passphrase properly:

1.  Check if the `HOME` environment variable exists on your system with `echo %HOME%` in CMD. If not then set it with `setx HOME C:\Users\<your home dir>` or from the GUI interface (Type Super key then search "environment variable").
2.  Install the package `ssh-agency` on Emacs.
3.  Add `(setenv "SSH_ASKPASS" "git-gui--askpass")` to your init file and `M-x eval-buffer`.

If the problem doesn't go then it may be that ssh-agent isn't started on your system. You can try to start it by opening a new Git bash window or refering to this [section](#error-ssh-agency-cprogra1gitusrbinssh-addexe-failed-with-status-1).

### Using Magit on Emacs on Linux

You may bump into this problem if you're using Magit on Emacs on Linux. For example, when my Fedora 26.2 was updated to 26.3 this problem occurred. You should check if the variable `SSH_AUTH_SOCK` is set for Emacs. Type `M-x getenv RET SSH_AUTH_SOCK` to see if it exists or has a value. If not then check the value of this variable on your system with `$ echo $SSH_AUTH_SOCK`. For me it returns `/run/user/1000/keyring/ssh`. Then set the said variable for Emacs with the returned value by typing `M-x setenv RET SSH_AUTH_SOCK RET <returned value>`.

### Error (ssh-agency): ‘c:/PROGRA\~1/Git/usr/bin/ssh-add.exe’ failed with status 1

It's because ssh-agent isn't started or added to your Emacs environment. Run in shell:

``` bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/<private key file>
echo $SSH_AUTH_SOCK
```

Then in Emacs:

```
M-x setenv RET SSH_AUTH_SOCK RET <returned value>
```
