# Using third-party JAR files

We can copy JAR files to `%SOAPUI_HOME%/bin/ext/` and use them in Groovy source codes. See details in the following links:

* <https://community.smartbear.com/t5/SoapUI-NG/How-to-access-external-Jar-files-through-SoapUI-Pro/td-p/39660>
* <https://www.soapui.org/extension-plugins/old-style-extensions/developing-old-style-extensions.html>

# Handling HTTP compression by SoapUI Maven Plugin

When calling Facebook test-users API in SoapUI, it returns the response body with HTTP compression ("Content-Encoding: gzip") according to default SoapUI settings. However, SoapUI Maven plugin handles HTTP compression differently.

We need to add extra settings and overwrite the default behavior:

* Prepare "soapui-settings.xml" file with the following content. Other options are not required and the default values are applied.

    <?xml version="1.0" encoding="UTF-8"?>
    <con:soapui-settings xmlns:con="http://eviware.com/soapui/config">
      <con:setting id="HttpSettings@response-compression">false</con:setting>
    </con:soapui-settings>

* Attach "soapui-settings.xml" into Maven POM file:

    ...
    <plugins>
      <plugin>
        <groupId>com.smartbear.soapui</groupId>
        <artifactId>soapui-maven-plugin</artifactId>
        <version>5.2.1</version>
        <configuration>
          ...
          <settingsFile>src/test/resources/soapui-settings.xml</settingsFile>
          ...
        </configuration>
        ...
      </plugin>
    </plugins>
    ...

* Review the log entry and see if "soapui-settings.xml" is actually applied.

    17:02:48,808 INFO  [DefaultSoapUICore] initialized soapui-settings from [/home/yenbo.huang/test-project/src/test/resources/soapui-settings.xml]

Refer to the following pages for more details:
* <https://en.wikipedia.org/wiki/HTTP_compression>
* <https://www.soapui.org/test-automation/maven/maven-2-x.html>
* <https://community.smartbear.com/t5/SoapUI-Open-Source/SOAPUI-Response-returns-weird-characters/td-p/17273>
* <https://sites.google.com/a/henix.fr/wiki-squash-ta/faq/soapui/compressed-response>
* <https://developers.facebook.com/x/bugs/197793537085207/>
