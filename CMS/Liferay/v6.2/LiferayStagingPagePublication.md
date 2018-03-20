# Liferay staging area

* Supported modes
  * (Recommended) Remote Live
  * Local Live

# Contents can be staged

* Used in company projects
  * Application display templates
  * Documents and media
  * Dynamic data lists
  * Web content
* Others
  * Blogs
  * Bookmarks
  * Calendar
  * Message boards
  * Mobile device families
  * OpenSocial gadget publisher
  * Polls
  * Wiki

# Page versioning

* Allow site admin to create multiple variation of staged pages for allowing concurrent development.
* Create/merge/publish variations by Git-like versioning system.

# Using page variations

* Only affect pages, not contents.
* Only one page variation can be marked as “Ready for publication”.
* It’s possible to set permissions on each variation.

# Using “Local Live” staging

* Pros
  * Publish sites quickly.
* Cons
  * Not well protected and backed up.
  * Only one version of portlet can be installed in one Liferay server.

# Use “Remote Live” staging

* Should be enabled for a site as early as possible.
  * It’s not a good idea to publish huge data set to remote server.
* Require pre-configuration for local/remote servers.
* Account management
  * Require identical user credentials exist in local/remote servers.
  * Use LDAP and make account management easier.
    * Liferay virtual LDAP server.

# References

* User manual <https://dev.liferay.com/documents/10184/510059/indexed-using-liferay-portal-62.pdf>
* Liferay virtual LDAP server <https://web.liferay.com/marketplace/-/mp/application/15186785>