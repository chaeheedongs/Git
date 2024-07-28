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
  * [Git 커밋 내역 삭제하기](#Git-커밋-내역-삭제하기)
  * [Git 커밋 내역만 돌아가기](#Git-커밋-내역만-돌아가기)
  * [Git 태그 달기](#Git-태그-달기)
  * [Git 브랜치 생성하기](#Git-브랜치-생성하기)
  * [Git 브랜치 이동하기](#Git-브랜치-이동하기)
  * [Git 브랜치 합치기](#Git-브랜치-합치기)
  * [Git 일부 커밋 가져오기](#Git-일부-커밋-가져오기)
  * [Git 브랜치 이름 바꾸기](#Git-브랜치-이름-바꾸기)
  * [Git 브랜치 삭제하기](#Git-브랜치-삭제하기)
  * [Git 브랜치 강제 삭제하기](#Git-브랜치-강제-삭제하기)
* [GitHub](#GitHub)
  * [GitHub 로컬 Git 연동하기](#GitHub-로컬-Git-연동하기)
  * [GitHub 로컬 Git branch 생성하기](#GitHub-로컬-Git-branch-생성하기)
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

> git commit -m "[ message ]"

```shell
# 스테이징(저장)된 정보를 커밋한다.
$ git commit -m "- commit message"

[master 04f922b] - commit message
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 d.txt
 create mode 100644 e.txt
```

<br/><br/><br/>



## Git 커밋 내역 삭제하기

Git에서 변경된 사항을 삭제하거나  
어느 기점으로 돌아갈 때  
그 기쩜 이후의 커밋들을 모두 삭제한다.  

* 옵션
  * --hard
    * 변경된 사항을 모두 폐기처분 한다.
  * --mixed
    * 변경된 사항을 unstage로 남긴다.
  * --soft
    * 변경된 사항을 stage로 남긴다.

> git reset [ --hard, --mixed, --soft ] [ hash ]

<br/><br/><br/>



## Git 커밋 내역만 돌아가기

Git에서 변경된 사항 기점으로 돌아간다.  
이 때 메시지는 `'-Revert ~~~` 로 표기 되며,  
변경 사항 이후의 커밋들은 건들지 않는다.  

옵션으로 `--no--commit (-n)` 을 주면  
해당 기점의 변경 파일이 스테이지 단계로 보존된다.

> git revert [ --no--commit( -n ) ] [ hash ]

<br/><br/><br/>



## Git 태그 달기

Git의 어느 시점에 태그를 달아 표기 한다.

> git tag [ tag_name ]  
> git tag [ -m 'tag message' ] [ tag_name ]

<br/><br/><br/>



## GitHub에 푸쉬하기

> git push origin [ remote_branch ]

```shell
$ git push origin main
```

<br/><br/><br/>



## Git 브랜치 생성하기

현재 브랜치를 기준으로 브랜치를 생성한다.

> git branch [ branch_name ]

<br/>

브랜치 생성과 동시에 이동을 원할 때 `-c` 옵션을 사용한다.

> git switch -c [ branch_name ]

<br/><br/><br/>



## Git 브랜치 이동하기

현재 브랜치에서 다른 브랜치로 변경한다.  
이 때 수정하고 있는 파일이나 수정된 파일이 있다면  
해당 작업을 마무리 해 주어야 한다.

> git checkout [ branch_name ]  
> git switch [ branch_name ]

<br/><br/><br/>



## Git 브랜치 합치기

Git 브랜치를 합치는 방법은 두 가지가 존재한다.
* merge
* rebase

<br/>

merge는 현재 브랜치를 기준으로 다른 브랜치를 가져온다.  
merge를 하면 상단에 Merge 커밋이 생성되며 히스토리를 남긴다.

> git merge [ branch_name ]

<br/>

rebase는 현재 브랜치 커밋들을 다른 브랜치에 그대로 추가한다.  
rebase의 경우 다른 브랜치에 커밋이 추가가 되면 현재 브랜치를 제거한다.

> git rebase [ target_branch_name ]

<br/><br/><br/>



## Git 일부 커밋 가져오기

다른 브랜치에서 현재 브랜치로 커밋을 가져온다.  
보통 개발 중 핫픽스 된 커밋 내역이 필요할 때 사용한다.

> git cherry-pick [ branch_hash ]

<br/><br/><br/>



## Git 브랜치 이름 바꾸기

현재 브랜치의 이름을 변경한다.

> git branch -m [ branch_name ]

<br/><br/><br/>



## Git 브랜치 삭제하기

로컬 깃 브랜치를 삭제한다.  
로컬 브랜치가 원격 브랜치에 푸시 및 병합이 되어 있어야 삭제가 된다.

> git branch -d [ branch-name ]

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

> git branch -D [ branch-name ]

```shell
# -D
# Shortcut for --delete --force.
$ git branch -D feature/project
```

<br/><br/><br/>



## GitHub

<br/><br/>



## GitHub 로컬 Git 연동하기

로컬 프로젝트에 Git을 연동한 다음  
GitHub 홈페이지에서 로컬 Git 프로젝트를 연동하는 방법이다.  

```shell
# Local Git
$ git init
$ git add .
$ git commit -m '- init'
$ git branch -M main
$ git remote add origin https://~~~.git
$ git push -u origin main
```

<br/><br/><br/>



## GitHub 로컬 Git branch 생성하기

로컬 프로젝트에서 GitHub의 특정 브랜치를 기준으로  
브랜치를 생성하여 GitHub에 추가하는 방법이다.  

```shell
## 혹시 몰라 GitHub Repo와 내용을 업데이트 한다.
# Update Git Repository
$ git remote update
# Update Git Remote fetch
$ git fetch

# 특정(target) 브랜치를 기준으로 새 브랜치 생성
$ git checkout -b new_branch target_branch

# 브랜치를 GitHub에 추가
$ git push origin new_brach
```

<br/><br/><br/>

## GitHub 브랜치 삭제하기

원격 브랜치를 삭제한다.

> git push origin -d [ branch-name ]

```shell
$ git push origin -d feature/project 
```

<br/><br/><br/>