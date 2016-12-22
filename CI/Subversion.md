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

# Troubleshooting

## Importing self-signed CA

When connecting SVN to a host with self-signed CA (e.g., VisualSVN Server,) you have to import that CA into `$JAVA_HOME/jre/lib/security/cacerts` before using Eclipse Subversive plugin. Or, you will see the following error:

    Location information has been specified incorrectly.
    
    svn: E175002: java.lang.NumerFormatException: For input string: "ae"
    svn: E175002: OPTIONS request failed on '/svn/*****'