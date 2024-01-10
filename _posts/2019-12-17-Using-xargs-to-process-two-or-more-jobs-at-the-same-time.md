---
layout: post
comments: true
title: xargs 을 이용하여 두가지 이상의 작업을 동시에 처리하기
author: mac.automator
date: 2019-12-17 20:42
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

원문 http://guileschool.com/2019/12/17/Using-xargs-to-process-two-or-more-jobs-at-the-same-time/

질문사항
ls * | wc 명령을 실행할 경우 <ls 리스트> 도 화면에 보여주고, <wc> 처리결과도 화면에 보여주고싶어요

```shell
# <SOL> 로그 화면 캡쳐
user@linux:~/Desktop/text$ find . -iname '*.txt' -print0 | xargs -0 -n1 -I @ bash -c 'NAME="@"; ls $NAME; wc $NAME'
./thegeekstuff.txt
  8  45 297 ./thegeekstuff.txt
./path.txt
  2   3 162 ./path.txt
./number.txt
 3  3 28 ./number.txt
user@linux:~/Desktop/text$ 
user@linux:~/Desktop/text$ ls * | xargs -0 -n1 -I @ bash -c 'NAME="@"; ls $NAME; wc $NAME'
demo_file  fruits  number.txt  path.txt  thegeekstuff.txt
  7  48 234 demo_file
  3   3  24 fruits
  3   3  28 number.txt
  2   3 162 path.txt
  8  45 297 thegeekstuff.txt
 23 102 745 total
user@linux:~/Desktop/text$ 
```
