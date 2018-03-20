# Online resources

* Pro Git <https://git-scm.com/book/en/v2>
* Eclipse EGit <https://wiki.eclipse.org/EGit/User_Guide>
* Forking workflow <https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow>

# Terminology

* master
  * The default name for a starting branch when you run git init.
* origin
  * The default name for a remote when you run git clone. 
* Tracking branch and upstream branch
  * Checking out a local branch from a remote-tracking branch automatically creates what is called a "tracking branch".
  * And, the branch it tracks is called an "upstream branch".
  * Tracking branches are local branches that have a direct relationship to a remote branch.

# Config

Configurations are set in `~/.gitconfig`.

## Set username and email

    $ git config --global user.name "John Doe"
    $ git config --global user.email johndoe@example.com

## List settings

    $ git config --list

# Project

## Clone a project

    $ git clone https://github.com/libgit2/libgit2

# Files

## Showing file status and current branch name

Show complete details:

    $ git status

Show simple status:

    $ git status -s

## Add a file or directory

    $ git add <file or directory>

## Rename a file

    $ git mv <old file name> <new file name>

## Revert changes in working directory

    $ git checkout -- <file>

## Commit changes

Commit files (no need to use `git add`) with message:

    $ git commit -a -m <message>

Commit and open default editor:

    $ git commit

Commit with message:

    $ git commit -m <message>

Change commit message or add forgotten files:

    $ git commit --amend

## Remove a file or directory

    $ git rm <file or directory>

If you modified the file and added it to the index already, you must force the removal with the -f option:

    $ git rm -f <file or directory>

Keep the file in your working tree  but  remove  it  from  your  staging  area:

    $ git rm --cached <file or directory>

## Unstage a file

    $ git reset HEAD <file>

## Delete local commit one-by-one

    $ git reset --hard HEAD^

# Remote

## Showing remote information

    $ git remote -v
    $ git remote show <remote name>

## Add a new remote Git repository

Add a new remote Git repository as a remote name:

    $ git remote add <remote name> <url>

Add a remote for your local git that references upstream:

    $ git remote add upstream <url>

## Get data from remote and (try to) merge into working directory

    $ git pull

## Push changes to remote
 
    $ git push <remote name> <branch name>

Push "master" branch to "origin" server:

    $ git push origin master

# Branches

## Create/switch branch

Create a branch:

    $ git branch <branch name>

Switch to a branch:

    $ git checkout <branch name>

Create and switch to a branch

    $ git checkout -b <branch name>

## Push branch

Push a branch to remote:

    $ git push <remote name> <branch name>

Push a branch to where you pulled it:

    $ git push origin <branch name>

## See what tracking branches you have set up

    $ git branch -vv

## Merge changes

Merge branch back to master:

    $ git checkout master
    $ git merge <branch name>

Update master to branch:

    $ git checkout <branch name>
    $ git merge master

## Delete branch

    # git branch -d <branch name>

