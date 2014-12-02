# Sencha Workspace 사용법

http://docs.sencha.com/cmd/5.x/workspaces.html

## Generating a Workspace

**generate workspace** 를 하게되면 ExtJs 프로젝트를 관리하기위한 기본 작업공간이 만들어 진다.
아래와 같이 Sencha Cmd가 설치되어 있는 상태에서 아래의 커맨드 라인을 입력하여 워크스페이스를  생성한다.

```cmd
sencha --sdk-path <EXTJS5_APTH> generate workspace -ext my-workspace
```

위 커맨드를 실행하면 my-workspace라는 작업공간이 생성되는데 생성이 완료되면 ext 디렉토리에 ExtJS 4.2.1 or 5가 위치하게 되고 ext, packages 디렉토리가 생성됨

```cmd
$ sencha --sdk-path ~/sencha/Sdk/ext-5.0.1 generate workspace -ext my-workspace
$ cd my-worksapce
$ ls -la
total 0
drwxr-xr-x   5 seokangchun  staff  170 10 22 19:19 .
drwxr-xr-x   3 seokangchun  staff  102 10 22 19:19 ..
drwxr-xr-x   3 seokangchun  staff  102 10 22 19:19 .sencha
drwxr-xr-x  28 seokangchun  staff  952 10 22 19:19 ext       (ExtJS SDK)
drwxr-xr-x   2 seokangchun  staff   68 10 22 19:19 packages  (ExtJs Locale & Theme)
```

구조설명

```cmd
.sencha/                # Sencha-specific files (e.g. configuration)
    workspace/          # Workspace-specific content (see below)
        sencha.cfg      # Configuration file for Sencha Cmd
        plugin.xml      # Plugin for Sencha Cmd
```

".sencha/workspace/sencha.cfg" 파일에는 Sencha ExtJS 와 Sencha Touch SDK's의 프로퍼티 설정이 되어 있다.

```cmd
ext.dir=${workspace.dir}/ext              ----->  extjs 의 경우설정
touch.dir=${workspace.dir}/touch        ----->  touch 의 경우설정
```
## Workspace내 애플리케이션 설치

위에서 생성한 my-workspace내에 ExtJs의 theme-app-demo 애플리케이션을 아래와 같이 설치 한다.

`$ sencha -sdk ext  generate app themeAppDemo theme-app-demo`

```cmd
$ pwd
/Users/seokangchun/sencha/Workspace/my-workspace
$ sencha -sdk ext  generate app themeAppDemo theme-app-demo

$ ls -la
drwxr-xr-x   7 seokangchun  staff  238 10 22 19:35 .
drwxr-xr-x   3 seokangchun  staff  102 10 22 19:19 ..
drwxr-xr-x   3 seokangchun  staff  102 10 22 19:19 .sencha
drwxr-xr-x   3 seokangchun  staff  102 10 22 19:35 build
drwxr-xr-x  28 seokangchun  staff  952 10 22 19:19 ext
drwxr-xr-x   2 seokangchun  staff   68 10 22 19:19 packages
drwxr-xr-x  15 seokangchun  staff  510 10 22 19:35 theme-app-demo

$ cd theme-app-demo
$ ls -la
drwxr-xr-x  15 seokangchun  staff    510 10 22 19:35 .
drwxr-xr-x   7 seokangchun  staff    238 10 22 19:35 ..
drwxr-xr-x   3 seokangchun  staff    102 10 22 19:35 .sencha
-rw-r--r--   1 seokangchun  staff   1313 10 22 19:35 Readme.md
drwxr-xr-x   8 seokangchun  staff    272 10 22 19:35 app
-rw-r--r--   1 seokangchun  staff    316 10 22 19:35 app.js
-rw-r--r--   1 seokangchun  staff    107 10 22 19:35 app.json
-rw-r--r--   1 seokangchun  staff    294 10 22 19:35 bootstrap.css
-rw-r--r--   1 seokangchun  staff  50782 10 22 19:35 bootstrap.js
-rw-r--r--   1 seokangchun  staff    282 10 22 19:35 bootstrap.json
-rw-r--r--   1 seokangchun  staff   1472 10 22 19:35 build.xml
-rw-r--r--   1 seokangchun  staff    490 10 22 19:35 index.html
drwxr-xr-x   2 seokangchun  staff     68 10 22 19:35 overrides
drwxr-xr-x   2 seokangchun  staff     68 10 22 19:35 resources
drwxr-xr-x   7 seokangchun  staff    238 10 22 19:35 sass
```

Sencha Touch의 경우

```cmd
$> sencha -sdk /path/to/touch generate app TouchApp /path/to/workspace/touchApp
$> sencha -sdk /Users/seokangchun/sencha/Sdk/touch-2.4.1 generate app TouchDemo touch-demo
```

Workspace 구조
```cmd
.sencha/                    # Sencha-specific files (e.g. configuration)
    workspace/              # Workspace-specific content (see below)
        sencha.cfg          # Workspace's configuration file for Sencha Cmd
        plugin.xml          # Workspace plugin for Sencha Cmd

ext/                        # A copy of the Ext JS SDK
    ...

touch/                      # A copy of the Sencha Touch SDK
    ...

theme-app-demo/
    .sencha/                # Sencha-specific files (e.g. configuration)
        app/                # Application-specific content
            sencha.cfg      # Application's configuration file for Sencha Cmd

touch-demo/
    .sencha/                # Sencha-specific files (e.g. configuration)
        app/                # Application-specific content
            sencha.cfg      # Configuration file for Sencha Cmd

build/                      # The folder where build output is placed.
    production/             # Build output for production
        touchApp/
        extApp/
    testing/                # Build output for testing
        touchApp/
        extApp/
```

### Packages

공유 패키지 변경을 위해서는 ".sencha/workspace/sencha.cfg" 파일에 있는 `workspace.packages.dir`로 변경할 수 있다.

### workspace.classpath

자바스크립트 코드를 공유하기 위해 Workspace에 다른 애플리케이션이 필요한 경우 사용 됩니다.

Workspace에 Common 폴더를 추가한 경우

```cmd
.sencha/
    workspace/
    ...
common/             # Folder for common things between pages.
    src/            # Folder for common JavaScript code for all pages.
```

`workspace.classpath`를 아래와 같이 사용합니다.

```cmd
workspace.classpath=${workspace.dir}/common/src
```

복합 애플리케이션 workspace.classpath 구조

``` cmd
workspace.classpath=${workspace.dir}/common/src,${workspace.dir}/common2/src
```

