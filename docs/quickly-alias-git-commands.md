---
title: Quickly Alias Git Commands
date: 2020-01-16
slug: alias-git-commands

---
Typing Git commands over and over can get real tedious. Let's make it easier!

Run this command in your shell with your own alias name and the corresponding git command

`git config --global alias.{alias-name} {git command}`

\####Examples:
`git config --global alias.show-remote 'remote show origin'`

* command is now `git show-remote`

instead of:
`git remote show origin`

\#####You can even combine commands!
`git config --global alias.add-commit '!git add -A && git commit'`

* command is now `git add-commit -m 'My commit message'`

instead of:
`git add .`git commit -m 'my commit message'\`

Aliases can save you a lot of time! I'm always misspelling git commands but with aliases that is a thing of the past.

To see all your aliases run this command:

`nano ~/.gitconfig`

Near the bottom you'll see something like this

![](https://thepracticaldev.s3.amazonaws.com/i/jaluetce5mss7kqtsnvv.png)

**Disclaimer** 

With great power comes great responsibility. Use this command wisely! Make sure you know exactly what the command is doing before you alias or combine them.

Thanks 😁