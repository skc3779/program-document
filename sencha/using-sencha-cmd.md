## Sencha Cmd 사용법

### Sites

* Touch http://docs.sencha.com/cmd/5.x/touch/cmd_app.html
* Extjs http://docs.sencha.com/cmd/5.x/extjs/cmd_app.html

### Sencha Cmd

Cmd가 제공하는 기능

* Code Generation Tools

* JS Compiler

* Web Server

* Native Packaging

* Build Scripts

* Tuning Tools

* Workspace Management

* Image Capture

* Flexible Configuration system

* Logging

* Third-party Software

* Code Generation Hooks

### Sencha application web start

watch - Watches an application for file system changes and rebuilds.

```cmd
$ pwd
~/theme-app-demo
$ sencha app watch
```

sencha web -port XXX start

```cmd
$ sencha fs web -port 8000 start (포트번호 변경 후 구동)
```

### Sencha Cmd Upgrade  방법

새로운 업그레이드 버전을 체크

```cmd
sencha upgrade --check
```

마지막 버전으로 업그레이드

```cmd
$> sencha upgrade
```

### Creating a New Application

애플리케이션 생성 시 `-sdk` 옵션 명령어를 이용해 sdk를 지정 하여 생성 할 수 있다.

Sencha Touch Creating

```cmd
sencha -sdk /path/to/sencha-touch-sdk generate app MyExtJsApp /path/to/www/myapp
```

Sencha ExtJs Creating

```cmd
sencha -sdk /path/to/sencha-extjs-sdk generate app MyTouchApp /path/to/www/myapp
```

### Upgrading Your Application

애플리케이션 sdk를 업그레이드 하기 위해서는 아래와 같이 사용하면 된다.

```cmd
$> cd /path/to/www/myapp
$> sencha app upgrade /path/to/new_version_of_sdk
```

### Deploying Your Application

Sencha Cmd는 4가지의 빌드환경 옵션을 제공합니다.

* testing - intended for QA prior to production. All JavaScript and CSS source files are bundled, but not minified, which makes it easier to debug.
* package - creates a self-contained, redistributable production build that normally runs from the local file system without a web server.
* production - creates a production build that is normally hosted on a web server and serves multiple clients (devices). The build is offline-capable using HTML 5 application cache, and is enabled to perform over-the-air updates.
* native - first generates a package build, then packages it as a native application, ready to be deployed to native platforms.

```cmd
$> cd /path/to/www/myapp
$> sencha app build testing
$> sencha app build package
$> sencha app build production
```

### Generating Views 

Adding a view to your application is similar:

```cmd
$> pwd
~
$> sencha generate view -base <Base Class Name> <View Class Name>

foo.Thing creating
$> sencha generate view foo.Thing
app/
    view/
        foo/                    # Folder for the classes implementing the new view
            Thing.js            # The new view
            ThingModel.js       # The `Ext.app.ViewModel` for the new view
            ThingController.js  # The `Ext.app.ViewController` for the new view
```