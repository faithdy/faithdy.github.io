---
layout: post
title: Pro Git > Git Branch
category: "git"
tags: [git]
date: 2018-09-21 14:50
comment: false
---

## The Feature
- Git의 commit은 스냅샷들에 대한 commit object를 만들어 낸다.
- Branch는 이에 대한 Linked list.

## Merge
- Merge에는 fast-forward merge, 3-way merge가 존재.
- Fast-forward Merge  
![fast-forward-merge](https://git-scm.com/figures/18333fig0314-tn.png)
    - 위 사진은 master가 hotfix로 fast-forwarding됨.
    - target branch가 현재 branch를 base로 하는 경우, 현재 branch는 target branch의 latest commit으로 just fast-forwarding.
- 3-way merge  
![3-way-merge](https://git-scm.com/figures/18333fig0317-tn.png)
    - 위 사진은 master와 iss53이 3-way-merge됨.
    - target branch가 현재 branch를 base로 하지 않고 분기된 경우, 두 branch의 latest commit과 공통 조상 하나를 사용하여 3-way merge를 시작함.
    - merge commit이 발생.

## 브랜치 관리
- `git branch [--merged | --no-merged]`으로 merge가 완료되었는지, 아닌지 알 수 있음.
- 기본적으로 `--no-merged` option에 있는 branch는 삭제를 할 수 없음.
    - 삭제를 하려고 한다면 `-D` option으로 삭제를 시도 해야 함.

## 리모트 브랜치
- 리모트 트래킹 브랜치는 리모트 브랜치를 추적하는 브랜치.
- 이 브랜치는 로컬에 있지만 움직일 수 없다.
    - 워킹 디렉토리로 가져올 수 없다는 의미.
    - 서버와 같은 느낌으로 이해.
    - 북마크와 같은 느낌으로 이해.
- 리모트 서버로부터 리모트 트래킹 브랜치를 동기화 하는 방법
    - `git fetch (remote_name)`

## 브랜치 추적
- REMIND
    1. local repository, remote repository가 존재.
    2. `fetch`를 통해 remote에 있는 branch들을 가져올 수 있음.
    3. 이때, remote branch들은 움직일 수 없는 branch들.
    4. 따라서, local repository에 이들을 추적, 수정할 수 있는 branch를 생성해주어야 함.
- 리모트 트래킹 브랜치를 로컬 브랜치로 checkout하면 자동으로 트래킹 브랜치가 만들어 진다.
    - Remote branch를 *Upstream Branch* 라고 부름.
- local에 없을 때 추적하는 방법.
    - `git checkout -b [branch] [remotename]/[branch]`
    - `git checkout [remote branch]`
- local에 존재할 때 추적하는 방법.
    - `git branch [-u | --set-upstream-to] [remote name]/[branch]`
- 추적 상태 확인

    ```
    $ git branch -vv
    iss53         7e424c3 [origin/iss53: ahead 2] forgot the brackets
    master        1ae2a45 [origin/master] deploying index fix    
    * serverfix   f8674d9 [teamone/server-fix-good: ahead 3, behind 1] this should do it
    testing       5ea463a trying something new
    ```
    - **ahead** 는 remote branch로부터 local branch가 앞선 commit이 있다는 것.
    - **behind** 는 remote branch로부터 local branch가 뒤쳐진 commit이 있다는 것.
    - **ahead** 와 **behind** 가 안 보일 시, 위 *local에 존재 할 때 추적하는 방법* 으로 동기화할 것.

## Rebase
- Rebase는 3-way merge 상황을 선형 리스트로 만듦.
- Rebase, re-base, 즉, 두 branch간의 3-way 상황 시 fast-forwarding이 될 수 있도록 target branch를 base로 다시(re) 두겠다는 말.

  ![before](https://git-scm.com/figures/18333fig0327-tn.png)
- 위 상황에서 master를 merge하면, dev의 latest commit, master의 latest commit, 둘의 공통 조상을 바탕으로 merge commit이 생김.

  ![3-way-merge](https://git-scm.com/figures/18333fig0328-tn.png)
- 만약, experiment의 base가 **C2** 가 아니고 **C4** 라면?
    - master의 latest commit까지로 re-base하자.

  ![rebase](https://git-scm.com/figures/18333fig0329-tn.png)
- rebase는 **C3**이 아닌 **C3'** 을 만든다. 즉, commit 내용이 변경된다는 것.

## 고찰
- rebase는 history를 선형적으로 만들어 준다는 것에서 의미가 있다.
- 다만, rebase는 commit의 내용을 변경하므로 이미 remote repository에 올린 history에 대해서는 적용하지 말 것.
