# LAR files

* LAR = Liferay ARchive file
* Export LAR file and import it to another environment.

# Export a site

* Pages
  * Site pages
  * Site page settings
  * Theme settings
  * Logo
* Content
  * Categories
  * OpenSocial gadget publisher
  * Comments
  * Ratings
* Permissions
  * Permissions assigned to roles

# Portlet data import options

* Some portlets support data import/export.
  * Import options
  * Update data
    * Mirror
    * Mirror with overwriting
    * Copy as new
  * Authorship of the content
    * Use the original author
    * Use the current user as author

# Portlet data: Web Content

* Application
  * Configuration
    * Setup
* Content
  * Web content
    * Referenced content
    * Version history
  * Structures
  * Templates
  * Comments
  * Ratings
  * Deletions
* Permissions
  * Permissions assigned to roles

# Portlet data: Documents and Media

* Application
  * Configuration
    * Setup
* Content
  * Folders
  * Documents
    * Previews and thumbnails
  * Comments
  * Ratings
  * Deletions
* Permissions
  * Permissions assigned to roles

# Other portlet data

* Other portlet data can be exported
  * Dynamic data lists
  * Application display templates
* Export options
  * Permissions
    * Permissions assigned to roles

# The safe way to use LAR file

* Data could be corrupted when there are conflicts.
* The safe way to do it:
  * Delete the site entirely.
  * Create a new site with the same name.
  * Create new site/page templates.
  * Import site/page templates.
  * Import the LAR file into the new site.

# Limitations

* LAR file is not compatible between Liferay versions.
* Site/page templates must be imported before site import by LAR files.
* Don’t make this a regular occurrence.
  * Use Liferay’s staging environment instead.
    * See user manual CH 3.8.
* Don’t use LAR to backup sites.
  * This is not a complete backup solution.
  * Follow official backup procedures.
    * See user manual CH 19.1.