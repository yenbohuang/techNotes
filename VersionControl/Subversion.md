# Admin

    svnadmin create d:\svn-repo

# Client

    svn list --verbose -R file:///d:/svn-repo
    svn cleanup d:\mydir
    svn update -r30

# Common commands

    svn mkdir mydir
    svn mkdir -m "note" file:///d:/svn-repo/mydir

    svn checkout file:///d:/svn-repo/dir d:\mydir

    svn add myfile.txt
    svn commit -m "this is a comment"

    svn revert myfile.txt
    svn delete myfile.txt

    svn log --verbose myfile.txt
