---
title: 'How to Manage Dotfiles'
date: 2022-06-07T08:16:40+02:00
lastmod: 2022-06-07T21:37:50+02:00
draft: true
---

Switching between machines or installing new ones, i was quite tired having to copy/paste my dotfiles. (vim config, shell config, etc)
Now I'm only using a bare repository.

No complicated tools, no weird symlinks, just the power of Git.

## How it works

#### Classic repository

Repositories created with `git init` is composed of 2 things :

- the working directory, consisting of files and folders you work on
- inside this directory a `.git` folder, the brain of the repo, managing all git stuffs

#### Bare repository

Bare repositories separate these 2 things :
with `git init --bare` you generate a folder that is exactly like the `.git` folder of a classic repository. Then you can work on files placed elsewhere, and use this `.git` folder to version control those files.

## Make it works

To use this power for managing our dotfiles, we will use a folder named `dotfiles`, the _brain_ (like a `.git` folder). Then the $HOME folder of our system will be the working tree.

```bash
# init the brain
git init --bare $HOME/.dotfiles

# create an alias for ease of use
# --git-dir refers to the brain, --work-tree to the working folder
alias dotfiles '/usr/bin/git --git-dir=$HOME/.dotfiles --work-tree=$HOME'
```

[atlassian]: https://www.atlassian.com/git/tutorials/dotfiles
[what-is-bare]: https://www.saintsjd.com/2011/01/what-is-a-bare-git-repository/
