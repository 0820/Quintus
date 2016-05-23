##Adding js and css files into magento

All methods reside in `Mage_Page_Block_Html_Head` class, there are `addCss` and `addJs` methods. Syntax is pretty simple.

```xml
<action method="addJs">
    <script>scriptaculous/scriptaculous.js</script>
</action>
```

Both `<file>` and `<script>` work and magento will send the contents as the first argument.

There's second parameter that allow you to send.
```xml
<action method="addCss">
    <name>print.css</name>
    <params>media="print"</params>
</action>
 ```
 ---
 The path of a script added by addJs method is relative to Magento root /js directory. For addCss method it is relative to skin directory of your theme.
 ---
 In fact both those methods are just wrappers for universal `addItem` method which can add either CSS or JavaScript into your page.
 The basic syntax for `addItem` :
 ```xml
 <action method="addItem">
    <type>js</type>
    <name>lib/ds-sleight.js</name>
</action>
```
The type can be **js, js_css, skin_js, skin_css, link_rel** or **rss**
 
Syntax for `params`
```xml
<action method="addItem">
<type>skin_css</type>
<name>below_ie7.css</name>
<params />
<if>lt IE 7</if>
</action>
```
---
There are `if` and `condition` parameters for `addItem`.
You can use `condition` to create complicate configuration.
Syntax is:
```xml
<action method="addItem">
    <type>skin_css</type>
    <name>custom.css</name>
    <params />
    <if />
    <condition>this_custom_css_is_allowed</condition>
</action>
```
```xml
<reference name="head">
    <action method="setThisCustomCssIsAllowed">
        <flag>1</flag>
    </action>
</reference>
 ```
