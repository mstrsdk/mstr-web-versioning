# mstr-web-versioning


### Description

MicroStrategy Web appends the postfix "?v=-[mstr_version_hash]" to allow client side caching. This is good when you're working in environment with multiple versions of MicroStrategy but, if this is not the case and you would like to remove such postfix, you can incorporate this plugin in your MicroStrategy Web application

---

#### To remove the postfix added to each file served by MicroStrategy Web

As you have noticed before, most of the JS and CSS files served by MSTR have a postfix that looks like this:
```html
http://{mstr_url}/style/desktop.css?v=-[mstr_version_hash]
```
Where 
***v=-[mstr_version_hash]*** is a string that represents the hashed MicroStrategy Web Version value.

This postfix can be removed by adding a configuration file "*browserSettings.xml*" inside your plugin folder; the destination path is:

[plugin_folder_name]/WEB-INF/xml/config/**browserSettings.xml**

The content of such file should be:
```xml
<browser-settings version="1.0">
	<browser-setting name="dbf" value="32" />
</browser-settings>
```

With this, just restart your Web Server (Tomcat or other) and you will see that, most of the CSS and JSS files will not have this postfix anymore.

---

To test this, we can add a CSS file to change the color of button "Create" at Desktop page:
[plugin_folder_name]/style/**desktopPage.xml**

Content of file:

```css
@charset "UTF-8";

.mscld-create {
	background-color: orange !important;
}
```

We changed the background-color and restarted our web server to confirm the file didn't have the postfix "?v=-xxxxxxx"

---

This plugin was provided by [MSTR SDK](https://www.mstrsdk.com)

Written by [Daniel Parra](mailto:daniel@mstrsdk.com)

July 2017