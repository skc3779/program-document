# bower

Bower는 maven, gradle과 비슷하게 bower.json과 .bowerrc 두개의 파일로 설정이 관리가 됩니다.

* .bowerrc : Bower에서 source와 dist를 다운받을 위치를 지정합니다.
* bower.json : Bower에서 다운받을 외부 component의 버젼 및 Project의 name, version을 지정합니다. 이는 maven, gradle에서 project와 비슷한 값을 지정하게 됩니다.

## bower 설치위치 변경방법

.bowerrc 파일을 생성한 다음에 아래와 같은 스크립트를 작성하시면 됩니다.
주의할 점은 루트 디렉토리가 현재 설치하는 위치를 기본으로 하고 있다는 점입니다.

.bowerrc

```json
{
	"directory":"."
}
```

bower.json

```json
{
	"name": "dgrid",
 	"version": "1.0.0",
	"dependencies": {
		"dojo": ">=1.8.9",
		"dstore": "~1.0",
		"xstyle": ">=0.1.3",
		"put-selector": ">=0.3.6",
		"dijit": ">=1.9.3",
		"dojox": ">=1.9.3",
		"util": "dojo-util#>=1.9.3"
	}
}
```

## bower 설치

bower를 사용하기 위해서는 먼저 node.js를 설치하셔야 합니다. 이후 bower를 전역적으로 사용할 수 있도록 `npm install -g`  -g 글로벌 옵션을 이용해서 설치 해주시면 됩니다.

```cmd
$> sudo npm install -g bower
$> sudo npm install -g bower-installer
```

## boewer 활용방법

bower는 [maven repository](http://mvnrepository.com/) 와 같이 http://bower.io/search 에서 검색해서 찾는 것이 가능합니다.

