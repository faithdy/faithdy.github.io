---
layout: post
title: Git-Practice > Practice
category: "git"
tags: [git]
date: 2018-09-02 17:00
comment: false
---

## 1. Pull Request
- Pull Request는 협업 간 repository 활용 전략.
![PR_concept](https://camo.githubusercontent.com/ecad6c4a2c9f895f23aa28ce995e5f188d7d4283/687474703a2f2f692e696d6775722e636f6d2f746932703735642e706e67)
- 유지 보수 대상의 중앙 저장소(upstream)가 있고, 이에 대해 각 개발자는 해당 저장소를 fork하여 자신의 저장소(origin)로 가져옴.
- Local에서 편집 후 자신의 저장소 origin에 push한 후, 이러한 변경 사항을 반영하겠다(pull)는 요청을 upstream에 보냄.
- Why do this process? Why not push directly at upstream?
    - If not use thie process,
        - 작업물 간 conflict 발생 가능성 존재.   
        - review없이 바로 push되므로 side effect 가능성 존재.

## 2. Rebase
- Which one is clean?[^1]
- [Initial tree]  
![initial_tree](http://dogfeet.github.io/articles/2012/git-merge-rebase/orig.png)
1. merge but not rebase  
![merge_but_not_rebase](http://dogfeet.github.io/articles/2012/git-merge-rebase/merge3.png)
2. merge as rebase  
![merge_as_rebase](http://dogfeet.github.io/articles/2012/git-merge-rebase/rebase3-merge.png)


## 3. 중간 commit 수정
1. command this:
```
git rebase -i --root
```
2. change the commit that you want to change from **"pick"** to **"edit"**

3. modify commit message under command:
```
git commit --amend -m "mssg"
git rebase --continue
```

## 4. blame
- you can trace out any file using **blame**:
```
git blame <file name>
git show <commit ID>
```

---
[^1]:
    [Git: Rebase는 언제 어떻게 해야 할까?](http://dogfeet.github.io/articles/2012/git-merge-rebase.html)
