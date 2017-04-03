# Angular CLI

### 사이트
https://github.com/angular/angular-cli

### 설치
nodejs 6.9.xx 이상이 설치되어 있어야 함.

```bash
npm install -g @angular/cli
```

### 사용법 확인

```bash
ng help
```

### 프로젝트 생성

```bash
ng new hello-ng2
```

```bash
2017-02-11  오후 10:41    <DIR>          .
2017-02-11  오후 10:41    <DIR>          ..
2017-02-11  오후 10:38               245 .editorconfig
2017-02-11  오후 10:38               488 .gitignore
2017-02-11  오후 10:41    <DIR>          .idea
2017-02-11  오후 10:38             1,271 angular-cli.json
2017-02-11  오후 10:38    <DIR>          e2e
2017-02-11  오후 10:38             1,127 karma.conf.js
2017-02-11  오후 10:40    <DIR>          node_modules
2017-02-11  오후 10:38             1,233 package.json
2017-02-11  오후 10:38               757 protractor.conf.js
2017-02-11  오후 10:38             1,176 README.md
2017-02-11  오후 10:38    <DIR>          src
2017-02-11  오후 10:38             2,691 tslint.json
```

### 실행방법

```ng serve``` 하면 기본 Port 4200으로 실행됨.
```live-reload-port```하면 라이브 리로드 포트를 임의지정.

```bash
ng serve --host 0.0.0.0 --port 4201 --live-reload-port 49153
```

### 빌드하기

```bash
ng build
```

프로덕션용 빌드를 위해서는 명령어로 prod 옵션을 추가해야 함.

```bash
ng build --prod --env=prod
ng build --prod
```

### 그외 명령


```bash
ng test : 단위 테스트를 실행
ng e2e  : 종단 테스트(end to end tests)를 수행합니다.
```


```bash
```

```bash
```





