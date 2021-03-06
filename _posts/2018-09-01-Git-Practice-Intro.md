---
layout: post
title: Git-Practice > Intro
category: "git"
tags: [git]
date: 2018-09-01 17:45
update: 2018-09-03 23:55
comment: false
---

## Why do developers use git?
- need to control history about code, document.
    - Program design, architecture degisn은 눈에 보이지 않는 설계 작업. 항상 기록해두고 저장해두는 습관을 가져야 함.
    - But, if we don't use version control system such as Git, maybe we control history as rename the title.
    - In other words, it means that Git doesn't use this pattern:
        - [보고서.hwp](#), [최종보고서.hwp](#), [진짜 최종 보고서.hwp](#)...

- easy to use.
    - support 2 interfaces: *CLI*, *GUI*.

- good maintenance.
    - Git isn't centralized system. So, we aren't consider that crash, fail over about server.
    - Git has 3 spaces[^1], which we just do commit/push or not.

- too many vendors, plug-in.
    - Hosting site: Git-hub, Bitbucket.
    - plug-in: So many CI/CD tools(e.g. `jenkins`), Co-work tools(e.g. `jira`, `slack`).

## Some terminology
1. commit
    - commit은 의미 단위의 기록. semantic적 접근.
    - I think, commit은 호흡이다. 긴 호흡으로 프로그램을 뚝딱 만들고 끝내고 되지만, 너무 큰 프로젝트라면? 고른 호흡과 일정 단위의 check point가 필요함.

2. branch
    - 나무 가지란 의미의 branch.
    - 뿌리부터 일정 부분까지는 같으나, 특정 시점(commit 기준)에서 다른 작업을 진행할 때 격리된 공간을 만들어 줌.

3. checkout
    - 여러 commit in specific branch, 여러 branch...
    - jump to specific commit or branch using checkout.

4. stash
    - if you check out branch from A to B and some files are not committed yet, they also come along into branch B.
    - stash is temporary space, which it is not working directory and staging area.  


5. merge
    - just merge two branch into one.
    - some types of branch integration:
        - fast-forward merge
        - non fast-forward merge
        - merge-commit
        - rebase


6. fetch and pull
    - Fetch 는 가져와서 임시폴더 (.git)에 저장
    - Pull은 바로 현재branch에 merge작업을 동반

## The famous open-source projects in Git-hub
1. Node.js (https://github.com/nodejs/node)    
2. Angular.js (https://github.com/angular/angular.js)    
3. Spring-boot (https://github.com/spring-projects/spring-boot)    
4. Rust (https://github.com/rust-lang/rust)    
5. Redis (https://github.com/antirez/redis)    
6. Flask (https://github.com/mitsuhiko/flask)

---
[^1]:
    working directory, staging area, git directory(repository).
