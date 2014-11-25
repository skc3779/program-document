## GIT 가이드

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

