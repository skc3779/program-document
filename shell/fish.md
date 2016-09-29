## fish and oh my fish & Mac에 설치하기

#### What is my setup?
https://www.iterm2.com/
http://fishshell.com/
https://github.com/oh-my-fish/oh-my-fish

#### Installing iTerm2

https://www.iterm2.com/ 에서 iTerm2 다운로드 받아 Application 디렉토리에 카피한다.

#### installing fish (using brew)

```bash
$> brew install fish
```

#### Switching to fish

디폴트 쉘로 fish를 사용하고 싶다면 아래의 명령어를 사용해라.

```bash
chsh -s /usr/local/bin/fish
```

#### Installing Oh My Fish

oh my fish를 다운로드 받아 설치한다.

```bash
curl -L https://github.com/oh-my-fish/oh-my-fish/raw/master/bin/install | fish

```

#### Installing the agnoster theme

대표적인 anoster 테마를 설치한다.

```bash
omf list --> 설치된 테마를 확인한다.
omf install agnoster --> agnoster가 설치되어 있지않으면 설치명령어를 실행한다.
omf theme agnoster --> 기본 테마를 agnoster로 설정한다.
```

#### Fixing the font issue

agnoster 테마를 사용해서 더 좋은 경험을 갖으려면 아래의 폰트를 설치해 준다.

https://github.com/abertsch/Menlo-for-Powerline

특정 폴더에 아래와 같이 git을 이용해 Menlo 테마를 다운로드 받는다.

```bash
git clone https://github.com/abertsch/Menlo-for-Powerline.git
```

다운로드 받으면 Finder를 이용해 해당 폴더의 "Menlo for Powerline.ttf" 파일을 더블클릭 해서 서체를 설치한다.

1. iTerm2의 경우 Preferences > Profiles > Text. 에서 Regular Font 와 Non-ASCII의 폰트를 "Menlo for Powerline.ttf" 으로 변경한다.

2.Mac 터미널의 경우 터미널 > 환경설정 > 프로파일 > 서체 변경에서 "Menlo for Powerline.ttf"으로 변경해 준다.










