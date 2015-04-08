# Redmine 설치하기

## Mac 10.10 Yosemite에 설치하기

[Redmine 인스톨 방법 1 링크](
http://www.redmine.org/projects/redmine/wiki/RedmineInstallOSXMavericksServer)

[Redmine 인스톨 방법 2 링크](https://github.com/yakmoz/ref/blob/master/redmine/redmine_os_x.md)

[Redmine 업그레이드 방법 1 링크](http://www.redmine.org/projects/redmine/wiki/RedmineUpgrade)

아래는 요점사항을 정리한 내용임.

### 인스톨 준비사항

1) Mysql 다운로드 : http://dev.mysql.com/downloads/mysql

2) .bash_profile 파일에 환경패스 설정

```ini
export PATH=/usr/local/mysql/bin:$PATH
```

3) mysqladmin 패스워드 생성 후 로그인

4) 데이터베이스 생성 (기존에 데이터베이스가 있다면 Skip)

```sql
CREATE DATABASE redmine CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE USER 'redmine'@'localhost' IDENTIFIED BY 'my_password';
GRANT ALL PRIVILEGES ON redmine.* TO 'redmine'@'localhost';
```

5) `/usr/lib` 에 MySql client library 링크

```console
sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib  /usr/lib/libmysqlclient.18.dylib
```

## Redmine 준비사항

Redmine은 XCode에 내장되어 있는 Ruby로 빌드한다. 그러나 어떤 경우에는 GEMS이 누락되어 있습니다.

GEM을 이용해 rails bundler passenger를 인스톨한다.
```console
sudo gem install rails bundler passenger

```

다음은 apache2-passenger module을 빌드하기 위해 passenger를 사용 합니다.  그러나 apache 서버를 활용하지 않으면 설치할 필요가 없습니다. (난 설치안함)

```console

sudo passenger-install-apache2-module

```

/etc/apache2/httpd.conf 에 아래의 내용을 포함 시킵니다.

```
LoadModule passenger_module /Library/Ruby/Gems/2.0.0/gems/passenger-5.0.6/buildout/apache2/mod_passenger.so
   <IfModule mod_passenger.c>
     PassengerRoot /Library/Ruby/Gems/2.0.0/gems/passenger-5.0.6
     PassengerDefaultRuby /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby
   </IfModule>
```

## 추가설치 패키지

OSX Maverick에서 Image와 Chart를 보여주기 위해서는 아래의 패키지를 설치해야 한다.

* ImageMagick - http://cactuslab.com/imagemagick/ (Note there are two versions, one with free type which requires XQuartz to be installed - the basic version is sufficient.)
* Pgkconfig - http://macpkg.sourceforge.net
* rmagick - http://rubygems.org/gems/rmagick (sometimes the download during installation fails, it's easier to have it stored locally)

ImageMagick과 pkgconfig을 설치후에 Path 환경변수를 설정해 줍니다.

```ini
export PATH=/opt/ImageMagick/bin:/opt/pkgconfig/bin:$PATH
```

rmagick을 에러없이 인스톨 하려면 아래의 방법을 사용해 설치해 주세요. 이때 rmagick은 직접 로컬에 다운로드해 설치해 주는게 더 좋습니다.

```console
sudo C_INCLUDE_PATH=/opt/ImageMagick/include/ImageMagick-6/ PKG_CONFIG_PATH=/opt/ImageMagick/lib/pkgconfig/ gem install --local ~/Downloads/rmagick-2.14.0.gem
```

위 인스톨시 아래의 오류가 발생한다면

```java
unable to convert "\xCF" from ASCII-8BIT to UTF-8 for ext/RMagick/RMagick2.bundle, skipping
unable to convert "\xCF" from ASCII-8BIT to UTF-8 for ext/RMagick/rmagick.o, skipping
unable to convert "\xCF" from ASCII-8BIT to UTF-8 for ext/RMagick/rmdraw.o, skipping
```
rdoc을 업데이트 하세요.

```
gem update rdoc
```

## 추가설치 패키지 다른방법 (이방법 사용 설치)

brew을 이용해 설치하는 방법입니다. 이때에는 Path 환경변수를 넣어줄 필요가 없습니다.

아래를 보면 우선 magick ,pkgconfig 를 brew 로 설치하자. 그리고 마지막에 MagickWand.h 해더위치를 C_INCLUDE_PATH 를 통해서 알려주고 install 하면된다.

```
$ brew install imagemagick
==> /usr/local/Cellar/imagemagick/6.9.0

$ brew install pkgconfig
==> /usr/local/Cellar/pkg-config/0.28

$ C_INCLUDE_PATH=/usr/local/Cellar/imagemagick/6.9.0-3/include/ImageMagick-6 PKG_CONFIG_PATH=/usr/local/Cellar/imagemagick/6.9.0-3/lib/pkgconfig/ sudo gem install rmagick
Successfully installed rmagick-2.14.0
```


### Redmine 설치하기

http://www.redmine.org/projects/redmine/wiki/RedmineInstallOSXMavericksServer

특정볼더 밑에 redmine을 다운로드 받아 설치한다. 현재 2015/04/08 일 현재 3.0.1 (2015-03-16), 2.6.3 (2015-03-16) 버전이 나와 있습니다. 나의 경우에는 2.6.3 버전을 설치 하였습니다.

레드마인 설치 폴덩의 설정디렉토리에 파일을 하나 만들어야 합니다. 직접이동할 필요는 없습니다. config 디렉토리인데 그 안에 보면 database.yml.example 이라는 파일이 있고 이 파일을 database.yml 로 copy 해서 복사본 하나 만들어 줍니다.

```
$ copy config/database.yml.example config/database.yml

```

파일중 production 에 데이터베이스 정보를 수정해 줍니다. 

```
production:
  adapter: mysql2
  database: redmine
  host: localhost
  username: redmine
  password: my_password
```

이제 다시 bundle을 아래와 같이 실행하여 줍니다.


```
$ bundle install --without development test

```

인스톨중에 아래와 같은 오류가 발생한다면 `추가설치 패키지`을 설치해 줍니다.


이제 보안토큰이 오류없이 설치되었다면 

```
rake generate_secret_token
```

데이터베이스 마이그레이션을 해줍니다.

```
RAILS_ENV=production rake db:migrate
```

이제 언어를 설치해 줍니다. `ko`를 선택해 주세요.

```
RAILS_ENV=production rake redmine:load_default_data
```

마지막으로 Redmine을 아래의 명령어로 실행해 주시면 됩니다.

```cmd
sudo ruby script/rails server webrick -e production
```

이제 사이트는 아래의 URL로 오픈되어 있게 됩니다.

```cmd
http://localhost:3000
```

수고많이 하셨습니다.