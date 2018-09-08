---
layout: post
title: Pro Git > Git의 기초
category: "git"
tags: [git]
date: 2018-09-08 15:00
comment: false
---

## Why git has staing area?
 - you just want to commit the one of two features[^1].
 - helps reviewing and merge conflicts[^2].

## Staging area와 --cached에 대한 고찰
  - 명령어 `git diff`, `git rm`에 대한 고찰.
  - Untracked <--> Working Directory <--> Staging Area <--> Git Repository
  - without `--cached`, Working Directory <--> Staging Area
  - with `--cached`, Staging Area <--> Git Repository
  - 다만, `diff`나 `rm` 또한, Tracked file이여야 함.   

## Tag
  - usually use the release.
  - command : `git tag`, `git tag -l <tag name>`
  - there are two types of tag.
      - Lightweight : specific commit, can't be up-to-date commit of the branch.
      - Annotated : it's like official tag. it is with signature, date, messages, etc.
  - how to use the tag
      - `git tag -a <tag name> -m "<message>"`
      - the option `-a`, is annotation.
      - the option `-a` and `-m` are used in annotated commit.
      - how to do lightweight tag about previous commit.
          - `git tag <tag name> <commit's checksum>`
  - how to push the tag
      - `git push <remote name> <tag name>`
      - `git push <remote name> --tags`
  - how to check-out the tag
      - can only check-out the tag using `-b` option.
      - `git checkout -b <branch name> <tag name>`

## Alias
  - `git [--config] alias.<name> '<commmand>'`
  - in `<command>`, can run external command like:
    `git --config alias.run '!bundle exec jekyll serve'`

---
[^1]:
    [What does 'stage' mean in git?
](https://softwareengineering.stackexchange.com/questions/119782/what-does-stage-mean-in-git)

[^2]:
    [Why the index/staging area is so useful](http://gitolite.com/uses-of-index.html)
