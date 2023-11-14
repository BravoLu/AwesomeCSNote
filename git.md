# Git

```shell
// for windows
$ git config --global core.autocrlf true

// for linux or macOS
$ git config --global core.autocrlf input

// compare the staged to last commit
$ git diff --staged

// compare the working directory with index
$ git diff

$ git log --oneline

$ git show HEAD~1:bin

$ git ls-tree

// unstage certain files.
$ git restore --staged 
// change the file to the next environment. (work directory revert to-> index)
$ git restore 

// undo untracked files.
$ git clean

// restore file from certain branch --source= (the default value for this option is last environment )
$ git restore --source=HEAD~1 file1.js

// untrack the xxx file, but make the file existed in the local directory.
$ git rm --cached xxx

$ git mv file_form file_to 
// is equal to
$ mv file_form file_to
$ git rm file_form (git add file_form)
$ git add file_to

$ git status -p (patch) -stat --pretty=oneline

$ git ls-remote https://xxx
```

## Undoing Things

```shell
// commit too early and possibly forget to add some file.
// Tips: only amend commits that are still local and have not been pushed somewhere.
$ git commit -m "init"
$ git add forgotten_file
$ git commit --amend
```

## Unstaging a staged files

```shell
// 
$ git reset HEAD file.txt
```

## Unmodifying a Modified File

```shell
// it's a dangerous operation because Git just replaced that file with the last staged or commited version
$ git checkout -- README.md

// git restore can be used for unmodifying and unstaging.
// unstaged.
$ git restore --staged xxx.txt
// unmodify, it's dangerous too. restore (--staged) = reset + checkout
$ git restore xxx.txt
```

## Working with Remotes

```shell
$ git remote add <short_name> <url>

$ git fetch <remote>

$ git pull 

$ git push <remote> <branch>

// Inspecting a remote
$ git remote show <remote>

# renaming and removing remotes, specifically for fork
$ git remote rename <old_name> <new_name>
$ git remote remove <remote>

# git pull with URL
$ git pull https://github.com/onetimeguy/project


```

## Tag

* Two types: lightweight and annotated

```shell
// tagging later
$ git tag -a v1.3 <commit-id>
// sharing tags
$ git push <remote> <tagname>
// push all tags
$ git push <remote> --tags
// delete tag
$ git tag -d <tagname>
// delete remote tags
$ git push origin --delete <tagname>  | git push origin :refs/tags/v1.4-lw

# git checkout 
# the cmd below leads to a detached HEAD.
# If you commit from a detached HEAD, your branch will be unreachable.
$ git checkout v2.0.0 
# The correct operation is create a branch
$ git checkout -b <newbranch> <oldtag> 
```

## Alias

```shell
$ git config --config alias.co checkout
# run an external command, use `!`
$ git config --global alias.visual '!gitk'
```

## Branching

* Fast-forward: git simplifies things by moving the pointer forward because there is no divergent work to merge together.

```shell
$ git branch -d hotfix.  # delete a branch

# after fix the conflicts, just `git commit`, it has default commit message.

$ git branch --merged

$ git branch --move bad-branch-name corrected-branch-name
$ git push --set-upstream origin corrected-branch-name
$ git push origin --delete bad-branch-name
```

## Remote Branches

```shell
$ git clone -o <rename-branch-name>

$ git fetch <remote-host>
# you have to create a local branch yourself after fetching.
$ git checkout -b serverfix (origin/serverfix) 
# another cmd
$ git checkout --track origin/serverfix
# another cmd, if the name is the same as <remote>/<branch>
$ git checkout serverfix 
# if the name is different
$ git checkout -b <different_name> <remote>/<branch>
# 
$ git branch -vv
# update all remote and branch
$ git fetch --all
#
$ git push origin --delete <remotebranch>
```

## Rebasing

```shell
$ git rebase --onto master server client

$ git rebase <basebranch> <topicbranch>

```

### The perils of rebasing

1. Do not rebase commits that exist outside your repository and that people may have based work on.
2. Rebase local changes before pushing to clean up your work, but never rebase anything that you've pushed somewhere.

## Distributed Git

```shell
# to solve the problem 1, use 
$ git diff master...contrib

# cherry-pick
$ git cherry-pick e43a6
# revert: reverse operation of cherry-pick
$ git revert xxx 

# genrating a build number
$ git describe master

# Preparing a Release
$ git archive master --prefix='project/' | gzip > `git describe master`.tar.gz
```

1. If `master` is a direct ancestor of your topic branch, this isn't a problem; but if the two histories have diverged, the diff will look like your're adding all the new stuff in your topic brnach and removing everything unique to the `master` branch
2. `cherry-pick` is like a rebase for single commit. It's useful if you have a number of commits on a topic branch and you want to integrate only one of them.

## Terms

* topic branch.

* Blobs (files)
* Tree (directory)

* \r: Carriage return
* \n: Line feed
* `refspec` `fetch =` is a refspec  : adding the following line to fetch, your can get pull request as a local branch name `refs/remotes/origin/pr/*` when you typing `git fetch`  

  ```
  [remote "origin"]
  		url = https://github.com/libgit2/libgit2
  		fetch = +refs/heads/:refs/remotes/origin/*
  		fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
  ```

  
* `-u`: --set-upstream
* Think of `reflog` as Git's version of shell history.
* `^` caret `~` tilde
* The difference between `checkout` and `reset`

  * `checkout` is working-directory safe. `reset --hard` will simply replace everything across the board without checking
  * `reset` move the branch that `HEAD` points to, `checkout` move `HEAD` itself to point to another branch.


## Github flavored Markdown

* **Task List**

- [x] write the code
- [ ] Write all the tests.
- [ ] Document the code

* **Quoting** 

> This is quoted.

* emoji

:clap:

## Keep your GitHub public repository up-to-date

```shell
$ git remote add progit git:github.com/xxx
$ git fetch progit
$ git branch --set-upstream-to=progit/master master
$ git config --local remote.pushDefault origin
```

## Hook



## Commit Range

```shell
# shows the commit of experiment that is not involved in master branch
$ git log master...experiment
```



## Stashing and Cleaning

```shell
# If you don't want to do a commit of half-done work just so you can get back to this point later, you can use stash command.
$ git stash 

$ git stash apply --index # restaged the staged files.
$ git stash apply # will continue have it on your stack.
$ git stash pop # will drop it from stack

$ git stash branch <new branchname> # create a new branch for you with your selected branch name
```



## Rewriting History

```shell
# changing the last commit
$ git commit --amend

# use rebase -i to edit commit
$ git rebase -i 
```



## Merge Conflicts

1. Make sure your working directory is clean before doing a merge that may have conflicts.

```shell
$ git merge abort # revert back to your state before you ran the merge

# `-Xignore-space-change` ignores whitespace completely when comparing lines.
# `whitespace` treas sequences of one or more whitespace characters as equivalent
# This is a lifesaver if you have someone on your team who likes to occasionally reformat everything from spaces to tabs or vice-versa.
$ git merge -Xignore-space-change whitespace 
```



## Undoing Merge



## Submodule

```shell
# It will generate .gitmodules 
$ git submodule add https://xxx

# clone a repository with submodule
$ git clone 
$ git submodule init 
$ git submodule update
# =
$ git submodule update --init (--recursive)
# =
$ git clone --rescurse-submodules https://

# update submoduel
$ git submodule update --remote

# set the submodule.recurse to true
$ git config --global submodule.recurse true

# set config
$ git config push.recurseSubmodules on-demand(or check)

# foreach for submodule
$ git submodule foreach 'git stash'
```

