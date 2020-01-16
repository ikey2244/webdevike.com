---
title: Quickly Alias Git Commands
date: 2018-09-15 07:42:34
slug: quickly-alias-git-commands
---

Typing Git commands over and over can get real tedious. Let's make it easier! 

Run this command in your shell with your own alias name and the corresponding git command

```bash
git config --global alias.{alias-name} {git command}
```

## Examples

```bash
git config --global alias.show-remote 'remote show origin'
```

command is now

```bash
git show-remote
```

instead of:

```bash
git remote show origin
```

## Combine Commands
```bash
git config --global alias.add-commit '!git add -A && git commit'
```
command is now 

```bash
git add-commit -m 'My commit message'
```

instead of:
```bash
git add .`git commit -m 'my commit message'
```


Aliases can save you a lot of time! I'm always misspelling git commands but with aliases that is a thing of the past. 

To see all your aliases run this command:

```bash
nano ~/.gitconfig
```

Near the bottom you'll see something like this

![](https://thepracticaldev.s3.amazonaws.com/i/jaluetce5mss7kqtsnvv.png)

## Dislaimer

With great power comes great responsibility. Use this command wisely! Make sure you know exactly what the command is doing before you alias or combine them. 


Thanks 😁