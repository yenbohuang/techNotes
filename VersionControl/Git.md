# Online resources

* Pro Git <https://git-scm.com/book/en/v2>
* Eclipse EGit <https://wiki.eclipse.org/EGit/User_Guide>

For titles with labels:

* (EGit): It means that it is easier by using EGit.
* (CMD): It means that it is easier by using command-line.

# Config

Configurations are set in `~/.gitconfig`.

## (CMD) Set username and email

    $ git config --global user.name "John Doe"
    $ git config --global user.email johndoe@example.com

## (CMD) List settings

    $ git config --list

# Project

## (CMD) Clone a project

    $ git clone https://github.com/libgit2/libgit2

# Files

## (EGit) Showing file status and current branch name

Show complete details:

    $ git status

Show simple status:

    $ git status -s

## (EGit) Add a file or directory

    $ git add <file or directory>

## (CMD) Remove a file or directory

    $ git rm <file or directory>

If you modified the file and added it to the index already, you must force the removal with the -f option:

    $ git rm -f <file or directory>

Keep the file in your working tree  but  remove  it  from  your  staging  area:

    $ git rm --cached <file or directory>

## (EGit) Rename a file

    $ git mv <old file name> <new file name>

## (EGit) Revert changes in working directory

    $ git checkout -- <file>

## (EGit) Commit changes

Commit files (no need to use `git add`) with message:

    $ git commit -a -m <message>

Commit and open default editor:

    $ git commit

Commit with message:

    $ git commit -m <message>

Change commit message or add forgotten files:

    $ git commit --amend

## (CMD) Unstage a file

    $ git reset HEAD <file>

# Remote

## (EGit) Showing remote information

    $ git remote -v
    $ git remote show <remote name>

## (CMD) Add a new remote Git repository

Add a new remote Git repository as a remote name:

    $ git remote add <remote name> <url>

Add a remote for your local git that references upstream:

    $ git remote add upstream <url>

## (CMD) Get data from remote and (try to) merge into working directory

    $ git pull

## (CMD) Push changes to remote
 
    $ git push <remote name> <branch name>

Push "master" branch to "origin" server:

    $ git push origin master
