# Backup source codes

* Manage source codes by version control systems
  * Extend Liferay with an Ext plugin
    * Also store the version of Liferay source on which your extension environment is based.
  * Liferay plugins

# Backup file system

* Configuration file: “portal-ext.properties”
  * Backup this file at a minimum.
  * It’s generally the best to backup the whole AP server.
* Ehcache configuration
  * (Recommended) Follow plugin procedure and backup configuration file by version control system.
  * (Not recommended) Follow non-plugin procedure  and backup configuration file.
* The whole “/data” folder.
* Also backup “Document Library” location if you changed it.

# Backup database

* The backend database
  * E.g., MySQL, Oracle DB, etc.
* Documents and Media Library
  * Jackrabbit JSR-170 repository database.
* Search index
  * (Recommended) Cluster Link or Solr.
  * (Not recommended) In database.

# Patching Liferay

* Login customer portal with subscription account.
  * <https://web.liferay.com/group/customer>
* Download patch tool if yours is too old to patch
  * <https://web.liferay.com/group/customer/products/patching-tool>
  * Decompress and overwrite `liferay-portal-6.2-ee-sp8\patching-tool` folder directly.
* Select the product you purchased and download the patch
  * <https://web.liferay.com/group/customer/products/portal/6.2>
* Copy patch file to `liferay-portal-6.2-ee-sp8\patching-tool\patches`
* Shutdown Liferay
* Run `patching-tool.bat install` under `liferay-portal-6.2-ee-sp8\patching-tool\`.

# References

* User manual <https://dev.liferay.com/documents/10184/510059/indexed-using-liferay-portal-62.pdf>
