# Git

<br/><br/><br/>



## Index
* [Link](#Link)
* [Git](#Git)
  * [git 브랜치 삭제하기](#git-브랜치-삭제하기)
  * [git 브랜치 강제 삭제하기](#git-브랜치-강제-삭제하기)
* [GitHub](#GitHub)
  * [github 브랜치 삭제하기](#github-브랜치-삭제하기)
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



## git 브랜치 삭제하기

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



## github 브랜치 삭제하기

원격 브랜치를 삭제한다.

> git push origin -d < branch-name >

```shell
$ git push origin -d feature/project 
```

<br/><br/><br/>