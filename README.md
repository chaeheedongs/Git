# Git

<br/><br/><br/>



## Index
* [Link](#Link)
* [Git](#Git)
  * [Git 기본 정보 설정하기](#Git-기본-정보-설정하기)
  * [Git 프로젝트 생성하기](#Git-프로젝트-생성하기)
  * [Git 상태 확인하기](#Git-상태-확인하기)
  * [Git Remote 업데이트 하기](#Git-Remote-업데이트-하기)
  * [Git 브랜치 스테이징 하기](#Git-브랜치-스테이징-하기)
  * [Git 커밋하기](#Git-커밋하기)
  * [Git 브랜치 삭제하기](#Git-브랜치-삭제하기)
  * [Git 브랜치 강제 삭제하기](#Git-브랜치-강제-삭제하기)
* [GitHub](#GitHub)
  * [GitHub 브랜치 삭제하기](#Github-브랜치-삭제하기)
---

<br/><br/><br/>



## Link
* [공식 홈페이지](https://git-scm.com/)
* [다운로드](https://git-scm.com/downloads)
* [커맨드 설명](https://git-scm.com/docs)
* [가이드](https://git-scm.com/book/ko/v2)

---

<br/><br/><br/>



## Git

<br/><br/>


## Git 기본 정보 설정하기

Git에 대한 설정 리스트를 확인 할 수 있다.

> git config --global --list

<br/>

Git 이름과 메일 등록하기

> git config --global user.name [name]  
> git config --global user.email [email]

<br/>

Git 초기 생성시 master 브랜치가 아닌 main 브랜치로 생성되도록 설정하기

> git config --global init.defaultBranch main

<br/><br/><br/>



## Git 프로젝트 생성하기

최초 Git 프로젝트를 생성하는 방법이다.

> git init

```text
# git_project 디렉토리 생성
$ mkdir git_project

# 생성한 git_project 디렉토리 이동
$ cd git_project

# 내부 확인
git_project$ ls -al
total 0
drwxr-xr-x   2 admin  staff   64  6  3 14:20 .
drwxr-xr-x  26 admin  staff  832  6  3 14:20 ..

# git 최초 설정
git_project$ git init
git init                                                      ✔
Initialized empty Git repository in /Path/.git/

# 내부 .git 디렉토리 확인
git_project$ ls -al
drwxr-xr-x   3 admin  staff   96  6  3 14:23 .
drwxr-xr-x  26 admin  staff  832  6  3 14:20 ..
drwxr-xr-x   9 admin  staff  288  6  3 14:23 .gi
```


<br/><br/><br/>



## Git 상태 확인하기

로컬 Git의 변경 사항 및 상태등을 확인할 수 있다.

> git status

```text
usage: git status [<options>] [--] [<pathspec>...]

    -v, --verbose         be verbose
    -s, --short           show status concisely
    -b, --branch          show branch information
    --show-stash          show stash information
    --ahead-behind        compute full ahead/behind values
    --porcelain[=<version>]
                          machine-readable output
    --long                show status in long format (default)
    -z, --null            terminate entries with NUL
    -u, --untracked-files[=<mode>]
                          show untracked files, optional modes: all, normal, no. (Default: all)
    --ignored[=<mode>]    show ignored files, optional modes: traditional, matching, no. (Default: traditional)
    --ignore-submodules[=<when>]
                          ignore changes to submodules, optional when: all, dirty, untracked. (Default: all)
    --column[=<style>]    list untracked files in columns
    --no-renames          do not detect renames
    -M, --find-renames[=<n>]
                          detect renames, optionally set similarity index
```

```shell
# Staging 단계가 아닐 때
$ git status

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        d.txt # 빨간색으로 표기 됨

# Staging 단계로 변경
$ git add .

# Staging 단계일 때
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   d.txt # 초록색으로 표기 됨
```

<br/><br/><br/>



## Git Remote 업데이트 하기

GitHub에 있는 프로젝트 히스토리를 업데이트 한다.

> git remote update

<br/><br/><br/>



## Git 브랜치 스테이징 하기

로컬에 변경 및 추가된 내용을 Git에 스테이징(저장)한다.

> git add [file]  
> git add .

```shell
# e.txt 파일 생성
$ touch e.txt

# 파일 리스트 조회
$ ls -al
drwxr-xr-x 1 admin 197121 0 Jan  2 11:25 ./
drwxr-xr-x 1 admin 197121 0 Dec 29 15:01 ../
drwxr-xr-x 1 admin 197121 0 Jan  2 11:19 .git/
-rw-r--r-- 1 admin 197121 0 Dec 20 11:02 a.txt
-rw-r--r-- 1 admin 197121 0 Dec 20 11:12 b.txt
-rw-r--r-- 1 admin 197121 0 Dec 20 11:22 c.txt
-rw-r--r-- 1 admin 197121 0 Dec 20 11:25 d.txt
-rw-r--r-- 1 admin 197121 0 Jan  2 11:25 e.txt

# Git 상태 확인
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   d.txt # 스테이징(저장) 되어 있음

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        e.txt # 스테이징(저장) 되어 있지 않음

# e.txt 스테이징(저장) 하기
$ git add .

# Git 상태 확인
$ git status

On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   d.txt
        new file:   e.txt
```

<br/><br/><br/>



## Git 커밋하기

Git에 스테이징(저장)된 데이터를 커밋한다.

> git commit -m "< message >"

```shell
# 스테이징(저장)된 정보를 커밋한다.
$ git commit -m "- commit message"

[master 04f922b] - commit message
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 d.txt
 create mode 100644 e.txt
```

<br/><br/><br/>



## GitHub에 푸쉬하기

> git push origin [remote_branch]

```shell
$ git push origin main
```

<br/><br/><br/>



## Git 브랜치 삭제하기

로컬 깃 브랜치를 삭제한다.  
로컬 브랜치가 원격 브랜치에 푸시 및 병합이 되어 있어야 삭제가 된다.

> git branch -d < branch-name >

```shell
# -d --delete
# Delete a branch. 
# The branch must be fully merged in its upstream branch, 
# or in HEAD if no upstream was set with --track or --set-upstream-to.
$ git branch -d feature/project
```

<br/>

## git 브랜치 강제 삭제하기

로컬 깃 브랜치를 강제로 삭제한다. ( force )

> git branch -D < branch-name >

```shell
# -D
# Shortcut for --delete --force.
$ git branch -D feature/project
```

<br/><br/><br/>



## GitHub

<br/><br/>



## GitHub 브랜치 삭제하기

원격 브랜치를 삭제한다.

> git push origin -d < branch-name >

```shell
$ git push origin -d feature/project 
```

<br/><br/><br/>