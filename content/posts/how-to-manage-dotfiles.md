---
title: 'How to Manage Dotfiles'
date: 2022-06-07T08:16:40+02:00
lastmod: 2022-06-12T15:12:50+02:00
draft: false
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
# Init the brain
git init --bare ~/.dotfiles

# Create an alias for ease of use
# --git-dir refers to the brain, --work-tree to the working folder
alias dotfiles '/usr/bin/git --git-dir=$HOME/.dotfiles --work-tree=$HOME'

# Use git like a normal repo
dotfiles add ~/.vimrc
dotfiles commit -m 'add vim config'
dotfiles push -u origin main
dotfiles remote add origin git@github.com:fabious/dotfiles.git
dotfiles push -u origin main
```


#### Use with an already existing dotfiles repo

```bash
# To install the dotfiles
git clone --bare https://github.com/fabious/dotfiles.git ~/.dotfiles
alias dotfiles '/usr/bin/git --git-dir=$HOME/.dotfiles --work-tree=$HOME'
dotfiles checkout
dotfiles config --local status.showUntrackedFiles no
```

## Resources

* [atlassian] - The best way to store your dotfiles: A bare Git repository
* [what-is-bare] - What is a bare git repository?
* [my-dotfiles-repo] - My dotfiles repository


[atlassian]: https://www.atlassian.com/git/tutorials/dotfiles
[what-is-bare]: https://www.saintsjd.com/2011/01/what-is-a-bare-git-repository/
[my-dotfiles-repo]: https://github.com/Fabious/dotfiles
