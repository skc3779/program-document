# GIT 가이드

## GIT Repository 생성

github에 Repository를 생성하는 방법 3가지

#### 1. …or create a new repository on the command line

```txt
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/skc3779/workspace_luna_bookstore_sample.git
git push -u origin master
```

#### 2. …or push an existing repository from the command line

```txt
git remote add origin https://github.com/skc3779/workspace_luna_bookstore_sample.git
git push -u origin master
```

#### 3. ...or import code from another repository

You can initialize this repository with code from a Subversion, Mercurial, or TFS project.


## GIT Tag 생성 및 삭제

git tag를 생성하기 위해서는 `git tag -a <태크명>` 으로 태그를 생성한다.

```cmd
$> git tag -a v1.0.0 -m "create tag"  > 새로운 테그를 생성한다.
$> git --tags > 마지막 태그를  github에  push 한다.
```
git tag를 삭제하기 위해서는 `git tag -d <태그명>`으로 태그를 삭제한다.

```cmd
$> git tag -d v1.0.0
$> git push origin :refs/tags/v1.0.0
```

## GIT branch 생성 및 삭제

git branch를 생성하기 위해서는 `git branch -b <브랜치명>`으로 브랜치를 생성한다
```cmd
$> git checkout -b web-none-db
$> git push origin web-none-db
```

git branch를 삭제하기 위해서는 `git branch -d <브랜치명>`으로 브랜치를 삭제한다.

1) 로컬 브랜치를 확인한다 또는 원격 브랜치를 확인한다.

```cmd
$> git branch     >  로컬브랜치 확인
  master
* web-none-db     >  핸재 프로젝트의 브랜치

$> git branch -r  > 원격브랜치 확인
  origin/master
  origin/web-none-db
```

2) 먼저 로컬 브랜치 상태를 확인한 다음에 삭제하고자 하는 브랜치가 현재상태가 아니게 master로 변경한 다음에 삭제하고자 하는 로컬 브랜치를 삭제한다. 그리고 다시 `git branch`로 확인해 보면 삭제된 것을 확인 할 수 있을 것입니다.
```cmd
$> git checkout master
Switched to branch 'master'

$> git branch -d web-none-db
Deleted branch web-none-db (was 9b2aca0).

$> git branch
* master
```

3) 원격 브랜치를 삭제 하기 위해서 먼저 `git remote show origin`를 하게 되면 원격의 origin 상태를 확인 할 수 있다.
```cmd
$> git remote show origin
* remote origin
  Fetch URL: https://github.com/~/multi-web-demo.git
  Push  URL: https://github.com/~/multi-web-demo.git
  HEAD branch: master
  Remote branches:
    master      tracked
    web-none-db tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)

```

4) 그럼 원격 브랜치를 `git push origin :web-none-db` 명령어를 이용해서 삭제해 보도록 한다.

```cmd
eokangchun-ui-iMac:multi-web-demo seokangchun$ git push origin :web-none-db
To https://github.com/skc3779/multi-web-demo.git
 - [deleted]         web-none-db
```

5) 마지막으로 github에서 확인해 본다.

## remove directory form git and local git 폴더, 파일삭제하기

```cmd
git rm -r one-of-the-directories
git commit -m "Remove duplicated directory"
git push origin master
```

## Intellij 14에서 Git branch 변경하기

Project Menu (우측마우스) -> Git -> Repository -> Branch... 팝업메뉴 중에서 변경하고자 하는 브랜치를 선택











