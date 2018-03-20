# Using System.out

* “System.out” will print logs on console
* It can be redirected to a file

    catalina.bat run > catalina.out 2>&1

# Add category and adjust log level

* Control panel
  * System administration
    * Log levels
      * Add category
      * Adjust log level
* Log will be written in “liferay-portal-6.2-ee-sp8/logs/liferay.yyyy-MM-dd”

# Define logger in groovy

```
import com.liferay.portal.kernel.log.*;

Log logger = LogFactoryUtil.getLog("com.cardif");
logger.debug(“my message”);
```

# References

* Liferay 6.2 logging system <https://dev.liferay.com/discover/deployment/-/knowledge_base/6-2/liferays-logging-system>
