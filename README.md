# Tutorial Git

## Config

This is the first thing you have to do after installing git. Sets your name and email into config file.

```bash

# Sets user name
$ git config --global user.name "David Brown"
$ git config --global user.email davidbrown@example.com

```

## Basic

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

## Remote

Here we use Github client because it is easy to setup and begin.

```bash

# Adds Github repository as a remote origin
$ git remote add origin https://github.com/Username/projectName.git

# Pushes to the remote orgin
$ git push -u origin master

```

