# mstr-web-versioning
By MSTR SDK Group


#### Description

This MSTR Web SDK plugin attempts to:


#### Remove the postfix added to each file served by MicroStrategy Web

As you have noticed before, most of the JS and CSS files served by MSTR have a postfix that looks like this:
```html
http://{mstr_url}/style/desktop.css?v=-xxxxxxxxx
```
Where 
***v=-xxxxxxx*** is the postfix added by MicroStrategy Web and the value is a hash string of the MicroStrategy Web Version

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

Finally, we added a CSS file to change the color of button "Create" at Desktop page:
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