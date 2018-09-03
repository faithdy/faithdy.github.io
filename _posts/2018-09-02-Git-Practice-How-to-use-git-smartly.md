---
layout: post
title: Git-Practice > How to use git smartly
category: "git"
tags: [git]
date: 2018-09-02 21:00
comment: false
---

## Set up a strategy
- For good dish, we have make this features better:
    1. **maintenance**,   
    2. **maintenance** and
    3. **maintenance**...

- use our tools:   
    1. Commit
        - one commit is one meaning.
        - commit message is like *abstract* in the paper.
    2. Branch
        - one branch is one function/module.
        - e.g. devide a category into a branch.
            - origin/git, origin/info.

    3. Pull Request
        - PR is good co-work strategy using above tools.
        - communication using `code-review`.
        - can be verified by `CI/CD tools`.

    4. Rebase or Merge
        - control the history.
        - good tree flow is related to maintenance directly.
            - because it makes us trace out anything easily.

- Let's deep down..

## Commit
::MUST FILL OUT THIS::

## Branch[^1]
![type_of_branch](https://backlog.com/git-tutorial/kr/img/post/stepup/capture_stepup1_2_1.png)

1. Integration branch
    - 언제든지 배포할 수 있는 브랜치.
    - Must be stable!

2. Topic branch(feature branch)
    - 기능 추가나 버그 수정과 같은 단위 작업을 위한 브랜치.

---
[^1]:
    [브랜치 만들기 ](https://backlog.com/git-tutorial/kr/stepup/stepup1_2.html)
