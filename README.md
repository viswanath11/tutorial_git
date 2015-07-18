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

## Tips

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
