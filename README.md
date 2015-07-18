# Tutorial Git

## Config

### Username/email
This is the first thing you have to do after installing git. Sets your name and email into config file.

```bash

# Sets user name
$ git config --global user.name "David Brown"
# Sets user email
$ git config --global user.email davidbrown@example.com

```

### Additional setting

```bash

# Sees config help
$ git config --help

# Sees all config settings
$ git config --list

# Sets editor (default = vi/vim)
# when you input something while using git
$ git config --global core.editor emacs

# Sets pager (default = less)
$ git config --global core.pager 'more'
$ git config --global core.pager ''     # this disables any pager

# Enables autocorrect
$ git config --global help.autocorrect = 1 # enabled

# Color settings
$ git config --global color.ui true 	# Git defines colour pattern ( not terminal's default colour pattern)
$ git config --global color.ui false 	# No-colour


```

## Basic

### Initialize

```bash

$ cd projectDirectory

# Initializes as a git repository
$ git init

# Adds all local files in the directory
$ git add -A

# Sees the status and check files in staging
$ git status

# Commits with commit message
$ git commit -m "first commit"

# Sees the log of changes
$ git log

```

### Remote

Here we use Github client because it is easy to setup and begin.

```bash

# Adds Github repository as a remote origin
$ git remote add origin https://github.com/Username/projectName.git

# Pushes to the remote orgin
$ git push -u origin master

```

### Clone

By cloning, you can use exsiting repository.
Here is all available repository URL.

- ssh     :ssh//[user@]host.xz[:port]/path/to/repo.git
- git     :git//host.xz[:port]/path/to/repo.git
- http[s] :http[s]://host.xz[:port]/path/to/repo.git
- ftp[s]  :ftp[s]://host.xz[:port]/path/to/repo.git
- rsync   :rsync://host.xz/path/to/repo.git

```bash

$ git clone git@github.com:username/repositoryname.git

```

### Add/Reset

```bash

# By `add` command, files can be added to a staging area
$ git add .

# Adds by seeing each files one by one
$ git add -p .
$ git add -patch .

# Adds only files which have been already managed by git
$ git add -u .
$ git add -update .

```

If you want to goes back to working directory from staging areas, then use `reset` commands.

```bash

$ git reset

```

### Remove/Rename

Just deleting your files in Finder.app or explorer does not mean that those files would be deleted from Git. You have to user `git rm` command to delete those files info from Git as well. This is also the same when you rename files.

```bash

# Removes files
$ git rm sample.txt

# Renames files
$ git mv sample.txt renamed.txt

```

### Clean

You can delete files which are not managed by Git by `git clean`.

```bash

# Firstly, check which files would be deleted by `git clean -f`
$ git clean -n

# Then, delete those files
$ git clean -f

```

## Intermediate

### Stash

Use `git stash` when you want to temporary go back to the clean working directory without losing the current state. Git offers stash, some kind of temporal stages for saving changes but you do not want to add them yet.

```bash

# adds the current state to stash with stash message
$ git stash save "stash: stash test"

# lists stashed
$ git stash list

# reflects stash by stash index
$ git stash pop stash@{0} --index

# removes stash
$ git stash drop stash@{0}

# shows stash contents
$ git stash show stash@{0} -p

# clears all stash
$ git stash clear

```

### Reset/Reflog

#### Reset

```bash

# Firstly, checks commit ID
# * commit ID is a SHA-1 hashed string
$ git log

# then you can see commit logs like belows
...
commit 7a16aed234ef71f9a0d021cf9319a8783256a7e1
Author: WagatsumaKenju <ken901waga@gmail.com>
Date:   Sat Jul 18 16:29:17 2015 +0900

    done Remove/Rename
...

# then go backs to the commit point by the commit id
$ git reset 7a16aed234ef71f9a0d021cf9319a8783256a7e1

```

#### Reset Options

||`git reset --soft`|`git reset --mixed`|`git reset --hard`|
|---|---|---|---|
|Git directory			|Reset		|Reset		|Reset|
|Staging area 			|Unchanged|Reset		|Reset|
|Working directory 	|Unchanged|Unchanged|Reset|

#### Reflog

However how about you want to "reset the reset"? Then use `git reflog` to see changed history of HEAD branch.

```bash

$ git reflog
d46f725 HEAD@{0}: reset: moving to 7a16aed234ef71f9a...
2a2d92b HEAD@{1}: commit: ...commit messages... # you want to go back to this HEAD
338fbb3 HEAD@{2}: commit: ...commit messages...
7a16aed HEAD@{3}: commit: ...commit messages...
cfa988e HEAD@{4}: commit: ...commit messages...
8389e8c HEAD@{5}: commit: ...commit messages...
...

# then go backs to the HEAD@{1}
$ git reset --hard 2a2d92b

```

### Filter Branch

```bash

# remove all commits of sample.txt (including all commit points)
$ git filter-branch --tree-filter 'rm -f sample.txt'

```

## Tips

### `git log`

@see http://git-scm.com/docs/git-log
There are a lot of options for `git log` and most of them are very useful. It is worth knowing some of them.

```bash

# shows git log in one line
$ git log --oneline

# shows git log with decorated apperance
$ git log --graph

# shows git log with decorated apperance in one line
$ git log --oneline --graph

```

### `.gitignore`

@see
https://github.com/github/gitignore

When you want to delete some files which are already managed in Git, then follow below steps.

```bash

# Adds files which you want to remove from Git
$ echo ".DS_Store" >> .gitignore

# Removes target file from cache
$ git rm --cached .DS_Store


```

### Alias

```bash

# `checkout` can be called by `co`
$ git config --global alias.co checkout

# `commit` can be called by `ci`
$ git config --global alias.co commit


```
