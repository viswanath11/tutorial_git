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

### Add

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

## Remote

Here we use Github client because it is easy to setup and begin.

```bash

# Adds Github repository as a remote origin
$ git remote add origin https://github.com/Username/projectName.git

# Pushes to the remote orgin
$ git push -u origin master

```

## Tips

### Alias

```bash

# `checkout` can be called by `co`
$ git config --global alias.co checkout

# `commit` can be called by `ci`
$ git config --global alias.co commit


```
