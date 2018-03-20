# Use different template for the same data structure

* <https://web.liferay.com/web/sushilsaini/blog/-/blogs/same-web-content-showing-with-different-display-template->

# Getting path and querystring parameters

* How-to <https://web.liferay.com/community/forums/-/message_boards/message/536768>
  * Remember uncheck "template cacheable"

```
#set ($completeUrl = $request.get("attributes").CURRENT_COMPLETE_URL)
#set ($path = $httpUtil.getPath($completeUrl))
#set ($param = $httpUtil.getParameter($completeUrl, "param"))
```