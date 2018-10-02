---
layout: post
title: Pro Git > Git Tool
category: "git"
tags: [git]
date: 2018-09-24 20:42
comment: true
---

## Operator
- In command: **log** or **diff**,
- double dot A..B : B - A
- negative ^B, --notB : exclusive B
```
$ git log refA..refB
$ git log ^refA refB
$ git log refB --not refA
```
```
$ git log refA refB ^refC
$ git log refA refB --not refC
```
- tripple dot A...B : XNOR
```
$ git log master...experiment [--left-right]
```

## Stashing과 Cleaning
- Stash
    - 작업하던 일을 commit하기 전 다른 브랜치로 변경해야 할 때.
    - Definition : Modified이면서 Tracked 상태인 파일과 Staging Area에 있는 파일들을 보관해두는 장소.
    - `git stash [save] [--keep-index] [--include-untracked | -u]`
        - `--keep-index` 옵션은 Staging Area에 들어 있는 파일은 Stash하지 않음.
        - `--include-untracked` or `-u` 옵션은 untracked 파일도 같이 저장함.
    - `git stash list`
    - `git stash apply [stash@{id}] [--index]`
        - Stash는 load할 때, staged 상태였떤 파일을 자동으로 다시 staged상태로 만들어 주지 않는다.
        - `--index` 옵션은 staged 상태까지 적용 시킴.
    - `git stash drop stash@{id}`
    - `git stash pop`
    - `git stash branch <branchname> [<stash_id>]`
        - stash할 당시의 커밋을 checkout한 후 새로운 브랜치를 만들고 여기에 적용.
        - 성공하면 해당 stash를 삭제.
- Clean
  ```
  $ git status -s
   M lib/simplegit.rb
  ?? build.TMP
  ?? tmp/

  $ git clean -n -d
  Would remove build.TMP
  Would remove tmp/

  $ git clean -n -d -x
  Would remove build.TMP
  Would remove test.o
  Would remove tmp/
  ```
  - `-n` : 시뮬레이션(clean이 실행 될 시 지워질 리스트)
  - `-d` : recursive, working directory 하위까지 전부
  - `-x` : gitignore로 무시된 파일까지 삭제

## Git Grep & Log Search
- Git Grep
  - Unix Command **Grep** 과 유사.
  - 기본값은 워킹 디렉토리에서 검색
  - `git grep [-np | --count] {string}`
  - `-n` : 라인 번호
  - `--count` : 어떤 파일에서 몇개나 찾았는지를 표시
  - `-p` : 매칭되는 라인이 있는 함수 or 메소드 검색
- Log Search
  - 히스토리에 언제 추가되거나 변경되었는가?
  - `git log [-S<String> | -L :<string>:<file>]`
  - `-S`: 해당 문자열의 등장 및 변경 확인
  - `-L`: 어떤 함수나 한 라인의 히스토리를 확인

## 히스토리 단장하기
- Modify a latest commit
    - `git commit --amend`
- Modify the out-dated commits
    - `git rebase -i HEAD~{number}`
- Remove the commits and change the order
    - In **rebase**,
    ```
    pick f7f3f6d changed my name a bit
    pick 310154e updated README formatting and added blame
    pick a5f4a0d added cat-file
    ```
    - If you hope that remove commit *"added cat-file"* and change the order about the others,
    ```
    pick 310154e updated README formatting and added blame
    pick f7f3f6d changed my name a bit
    ```
- Squashing or Splitting the commit(s).
    - In **rebase**,
    - Squash : replace **pick** to **squash**, then Git merge that change and the change directly before it.
    - Splitting : replace **pick** to **edit**, then command this: `git reset HEAD^`, then do splitting.
- Filter-branch
    - like 포크레인.
    - e.g,
    ```
    $ git filter-branch --tree-filter 'rm -f passwords.txt' HEAD
    ```
    - `--tree-filter` : re-commit after run the rule.

## Git으로 버그 찾기
- File Annotation(Blame)
- Binary Search(Bisect)

## 서브 모듈
- Start the sub-module
    - `git submodule add {URL}`
- Clone the project with the sub-modules.
    ```
      `git clone {Top-module URL}`
      `git submodule init`
      `git submodule update`

      or

      `git clone --recursive {Top-module URL}`
    ```
- How to work
    - Simplest Way : 하위 프로젝트를 수정하지 않고 참조만 하면서 최신 버전으로 update하는 것.
    - Update sub-module
    ```
      $ cd (submodule/)
      $ git fetch
      $ git merge origin/master

      or
      $ git submodule update --remote (submodule/)
    ```
    - Modify sub-module

## Credential 저장소
- 암호를 매번 입력하지 않고 리모트 저장소에 접근하는 방법 : **cache**, **store**
  ```
  $ git config --global credential.helper cache
  $ git config --global credential.helper 'store --file ~/.my-credentials'
  ```
