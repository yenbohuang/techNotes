# Add new page

* Copy from existing content
* Web contents are referenced, not copied. Create new web contents for new requirements.
* Admin -> Site Administration -> Pages
  *  Look and Feel
    * Choose "Use the same look and feel of the public pages"

# Add web content

* Create new blank web content
* Create new data structure
* Create new template
  * Make sure parameters are matching with data structure

# Troubleshooting

* CSS conflict with Liferay CSS
  * Create another non-conflict theme
  * Switch to this theme, ignore layout skew and edit, switch back to original theme.
*  Customization Settings
  * Check "Customizable" checkbox by accident
    * Delete web content
    * Uncheck and save
    * Re-add web content
* Every static file are assigned with an UUID, remember attaching UUID when reference the file.
  * If user moved the file to another folder, we can still reference it by UUID.
* When adding minified JS into Document and Media, it returns MIME type as HTML and won't work on some browsers.
  * Use original JS for this scenario.

