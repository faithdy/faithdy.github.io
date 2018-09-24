---
layout: post
title: Pro Git > Git Server 그리고 분산환경에서의 Git
category: "git"
tags: [git]
date: 2018-09-24 17:30
comment: false
---

## Protocol
- there are 4 types of protocol.
    - Local protocol
    - HTTP protocol
    - SSH protocol
    - Git protocol
- Local protocol
    - NFS, Shared File System.
    - `git clone file::///srv/git/project.git`
- HTTP protocol
   - under the HTTP document,
   - just put **Bare** repository.

## Construct Git Server
```
  $ git clone --bare my_project my_project.git
  $ scp -r my_project.git user@git.example.com:/srv/git
```
```
  $ git clone user@git.example:/srv/git/my_project.git
```

## Workflow strategy
- Integration-Manager
    ![Integration-Manager](https://git-scm.com/book/en/v2/images/integration-manager.png)
- Dictator and Lieutenants
    ![DictatorAndLieutenants](https://git-scm.com/book/en/v2/images/benevolent-dictator.png)

## Contribution strategy
- If there are so many developer into one repository, how does codes clean?
- which one is best workflow in your project?
- take the access control? only read? or write&read?

## Commit strategy
- 공백 문자 제거
- 하나의 커밋에는 하나의 이슈, 수정사항만
- merge commit을 제외한 로그 : `git log --no-merges`

## 프로젝트 관리
- 프로젝트 관리자 (Upstream 관리자)는 다른 기여자의 커밋을 받을 떄, 바로 Master에 merge하지 않고, 테스트 브랜치를 만들어 통합 테스팅 후 Master에 merge하는 것도 하나의 전략.
- *master* branch에서 sc라는 사람이 작업한 Patch를 위한 브랜치 생성
    - `git branch sc/ruby_client master`
    - 이렇게 토픽 브랜치를 만들고 받은 Patch를 적용해보고 적용한 내용을 다시 Long-Running 브랜치(Master, Release, Production과 같은 안정된 브랜치)로 Merge 한다.
- 분기된 시점에서의 로그만 보기
    - `git log contrib --not master`
    - `git log master..contrib`
    - `-p` option으로 각 커밋에서 실제로 무슨 내용이 변경되었는지 확인 가능.
- Release 브랜치의 계층화도 안정화를 위한 하나의 전략.
    - master > develop > integrate
- history를 선형으로 유지하는 전략: **rebase** or **cherry-pick**
- A브랜치의 내용을 B브랜치로 옮기는 방법 : 위의 history 단장하는 전략 or **squash**.
