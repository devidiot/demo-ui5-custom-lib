# demo-ui5-custom-lib


## Prerequisites
Install the following npm packages (globally) to your development environment.

```
yarn : npm install -g yarn
yoman : npm install -g yo
generator-ui5-library : npm install -g generator-ui5-library
generator-easy-ui5 : npm install -g generator-easy-ui5
```


## /package.json
```
{
  "name": "test-workspace",
  "version": "1.0.0",
  "description": "",
  "keywords": [],
  "author": "",
  "license": "ISC",
  "private": true,
  "workspaces": [
    "packages/*"
  ]  
}
```


## Lib 및 App 생성
```
yo ui5-library
yo easy-ui5 project
```



## /app/package.json
```
  "dependencies": {
    "lib": "1.0.0"
  },
  "ui5": {
    "dependencies": [
      "ui5-middleware-livereload",
      "lib"
    ]
  }

```


# Resolving packages
```
yarn
```



## /app/../Main.view.xml
```
<mvc:View controllerName="org.starj.app.controller.MainView"
    xmlns:mvc="sap.ui.core.mvc" displayBlock="true"
    xmlns:lib="org.starj.lib"
    xmlns:lib-m="org.starj.lib.m"
    xmlns="sap.m">
    <Page id="page" title="{i18n>title}">
        <content>
            <lib:Example text="Example using custom library"></lib:Example>
            <lib-m:Text text="org.starj.lib.m.Text" color="red" fontWeight="bold"></lib-m:Text>
        </content>
    </Page>
</mvc:View>
```


## /app/../index.html 
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Title of org.starj.app</title>
    <style>
        html, body, body > div, #container, #container-uiarea {
            height: 100%;
        }
    </style>
    <script
        id="sap-ui-bootstrap"
        src="/resources/sap-ui-core.js"
        data-sap-ui-theme="sap_fiori_3"
        data-sap-ui-resourceroots='{
            "org.starj.app": "./"
        }'
        data-sap-ui-oninit="module:sap/ui/core/ComponentSupport"
        data-sap-ui-compatVersion="edge"
        data-sap-ui-async="true"
        data-sap-ui-frameOptions="trusted"
    ></script>
</head>
<body class="sapUiBody sapUiSizeCompact" id="content">
    <div
        data-sap-ui-component
        data-name="org.starj.app"
        data-id="container"
        data-settings='{"id" : "org.starj.app"}'
        data-handle-validation="true"
    ></div>
</body>
</html>
```






참조 : https://blogs.sap.com/2021/04/06/how-to-consume-ui5-custom-libraries-in-bas-or-vs-code

