# Sencha Extjs 구조


```cmd

$ sencha --sdk-path ~/developers/sencha/Sdk/ext-5.1.0 generate app ext5 MyExtJS5
$ cd MyExtJ%5
$ ls -la
SeoKangChunui-iMac:MyExtJS5 seokangchun$ ls -la
total 304
drwxr-xr-x  18 seokangchun  staff    612  3  4 00:32 .
drwxr-xr-x   4 seokangchun  staff    136  3  4 00:32 ..
drwxr-xr-x   4 seokangchun  staff    136  3  4 00:32 .sencha
-rw-r--r--   1 seokangchun  staff   2143  3  4 00:32 Readme.md
drwxr-xr-x   7 seokangchun  staff    238  3  4 00:32 app
-rw-r--r--   1 seokangchun  staff    705  3  4 00:32 app.js
-rw-r--r--   1 seokangchun  staff  10310  3  4 00:32 app.json
-rw-r--r--   1 seokangchun  staff    294  3  4 00:32 bootstrap.css
-rw-r--r--   1 seokangchun  staff  57519  3  4 00:32 bootstrap.js
-rw-r--r--   1 seokangchun  staff  58752  3  4 00:32 bootstrap.json
drwxr-xr-x   3 seokangchun  staff    102  3  4 00:32 build
-rw-r--r--   1 seokangchun  staff   1464  3  4 00:32 build.xml
drwxr-xr-x  13 seokangchun  staff    442  3  4 00:32 ext
-rw-r--r--   1 seokangchun  staff    354  3  4 00:32 index.html
drwxr-xr-x   2 seokangchun  staff     68  3  4 00:32 overrides
drwxr-xr-x   2 seokangchun  staff     68  3  4 00:32 packages
drwxr-xr-x   3 seokangchun  staff    102  3  4 00:32 resources
drwxr-xr-x   8 seokangchun  staff    272  3  4 00:32 sass

```

**제너레이터 되는 앱내부의 생성된 파일에 대해 알아보자.**

* .sencha : 앱과 관련된 설정파일이 위치한다. 빌드 및 개발과 관련된 세부 속성을 변경할 때 관련 파일을 수정할 수 있다.
* Readme.md : 마크업으로된 애플리케이션에 대한 미리보기 파일
* app : 앱에 실행되는 모든 클래스 파일이 위치하게 됩니다. MVC구조에 해당하는 폴더가 내부에 존재합니다.
* app.js : 앱의 인트로 클래스입니다. 이 글래스로 실핼될 수 있는 앱의 형태를 띄게 됩니다.
* app.json : 앱의 설정 파일입니다. 테마변경, 외부 패스 설정, 로케일, 다중 테마, 차트 등을 사용 할 수 있도록 설정합니다.
* bootstrap.css : 앱에 연결된 테마파일 링크가 위치합니다. 이 파일은 `sencha app watch`명령으로 개발시 build 폴더 내부의 development를 참고하게 되며, `sencha app build` 명령으로 실행시 production 폴더를 참조합니다.
* bootstrap.js : 앱이 실행될 때 사용되는 index.html 파일에서 앱을 로딩하기 위해 이 파일을 로드합니다. 이 파일은 앱을 실행 하는 데 관련된 모든 파일을 로드 할 수 있습니다.
* bootstrap.json : 센차 Cmd가 생성하며 계속 변경됩니다. senchar app build 또는 sencha app watch 명령이 새로 추가된 클래스 또는 필요한 모든 파일 정보를 기록합니다. 이 파일은 bootstrap.js가 호출하므로 사용자가 수정하지 않습니다.
* build.xml : 아파치 Ant를 이용해 빌드 프로세스를 변경할 때 사용합니다.
* ext : 앱 생성ㅇ시 참조한 -sdk 경로에 관련된 파일만 추출해 복사하여 앱이 실행될수 있게 합니다.
* index.html : 앱을 최종 실행하는데 필요한 파일입니다.app.json 내부에서 이 파일의 위치 및 이름을 변경할 수 있습니다. 
* overrides : 기존 클래스를 변경하지 않고 오버라이드해 변경된 내용으로 작동 할 수 있는 클래스 코드를 추가합니다.
* packages : 별동의 테마파일이나 패키지가 위치합니다.
* resources : 이미지 등 리소소 파일이 위치합니다.
* sass : 테마 또는 사용자 스타일을 적용하기 위한 scss 파일이 위치합니다.
