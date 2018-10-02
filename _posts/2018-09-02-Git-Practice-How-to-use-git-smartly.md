---
layout: post
title: Git-Practice > How to use git smartly
category: "git"
tags: [git]
date: 2018-09-02 21:00
update: 2018-10-03 01:25
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
- Commit message is like the title of book.
- Finally, without `git diff`, and only with `git log`, somebody knows what this commit changes.
- Maintenance의 끝판왕.

- Convention
    - Style : 일관성
    - Content : 간결함, 명료함.
    - Metadata : how to refer PR, Issue #?

- Seven Rules for Wonderful Git commit[^1].
    1. 제목과 본문을 빈 행으로 분리한다.
    2. 제목 행을 50자로 제한한다.
    3. 제목 행 첫 글자는 대문자로 쓴다.
    4. 제목 행 끝에 마침표를 넣지 않는다.
    5. 제목 행에 명령문을 사용한다.
    6. 본문을 72자 단위로 개행한다.
    7. 어떻게 보다는 무엇과 왜를 설명한다.


## Branch[^2]
![type_of_branch](https://backlog.com/git-tutorial/kr/img/post/stepup/capture_stepup1_2_1.png)

1. Integration branch
    - 언제든지 배포할 수 있는 브랜치.
    - Must be stable!

2. Topic branch(feature branch)
    - 기능 추가나 버그 수정과 같은 단위 작업을 위한 브랜치.

---
[^1]:
    [How to Write a Git COmmit Message](https://chris.beams.io/posts/git-commit/)  
    
[^2]:
    [브랜치 만들기 ](https://backlog.com/git-tutorial/kr/stepup/stepup1_2.html)
