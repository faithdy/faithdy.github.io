---
layout: post
title: Common Sense > What does brackets mean?
category: "common"
tags: [info,common,convention]
date: 2018-09-09 01:00
comment: false
---

## Intro : The types of brackets.
  - <> : angle brackets.
  - [] : square brackets.
  - () : round brackets, called parentheses.
  - {} : curly brackets.

## Usage Message : brackets are commonly used like this.
  - <> : positional arguments.
      - `Usage : my_program <host> <port>`
  - [] : optional argument(s).
  - () : required arguments by default. (explicit).
  - {} : required argument from mutually exclusive arguments.
    
## Example
```
Usage: program [-aDde] [-f | -g] [-n number] [-b b_arg | -c c_arg] req1 req2 [opt1 [opt2]]
```
  - options w/o operands: a, D, d, e.
  - exclusive options : f, g with vertical bar.
  - options with operands : n.
  - required arguments : req1, req2.

## Reference
  - [Bracket - wikipedia](https://en.wikipedia.org/wiki/Bracket#Angle_brackets)
  - [Usage message - wikipedia](https://en.wikipedia.org/wiki/Usage_message)
  - [Docopt - Language for description of CLI](http://docopt.org/)
