# Create Maven theme project

* Cannot be run by Eclipse WTP "add service"
* Run by deploy scope

    mvn clean package liferay:deploy

# Making Themes Configurable with Settings

* How-to <https://dev.liferay.com/develop/tutorials/-/knowledge_base/6-2/making-themes-configurable-with-settings>
* Modify "liferay-look-and-feel.xml"
  * Use "setting configurable=true" for configurations on site admin page.
  * Refer to "init_custom.vm" for available parameters.
  * Remember assigning default values.

# Troubleshooting

* TODO Theme/portlet cannot coexist in the same project? <https://web.liferay.com/community/forums/-/message_boards/message/26629926>
