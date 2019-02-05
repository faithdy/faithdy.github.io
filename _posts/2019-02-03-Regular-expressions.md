---
layout: post
title: Grep and Regular Expressions
category: bash, regular expression
tags: [bash,regular_expressions]
date: 2019-02-03 20:50
comment: true
---

## Grep option
- `-n` : print the matching line.
- `-v` : without -v (word).
- `-c` : print the matching count.
- `-i` : ignore case-sensitive

## Regular Expressions
- ^(word) : starting with the string word. e.g., `grep ^root /etc/passwd`
- (word)\$ : ending with the string word. e.g., `ls -al | grep txt$`
- [yf] : matching if any y or f is contained



## Reference
- http://www.nextree.co.kr/p4327/
- https://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html
