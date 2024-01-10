---
layout: post
comments: true
title: 쉘스크립트에서 IFS=$'\n' 의 의미
author: mac.automator
date: 2022-09-01 12:43
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

원문 http://guileschool.com/2022/09/01/2022-09-01-Reasons-for-using-IFS-$quotes-in-shell-scripts/

질문사항
쉘스크립트에서 IFS=$'\n' 는 어떤 목적을 가지고 있나요?

```shell
# 실제 변수에 저장되는 문자열이 다르다
bash-5.1$ F="\n"
bash-5.1$ echo -n "$F" | hexdump -C
00000000  5c 6e                                             |\n|
00000002
bash-5.1$ F='\n'
bash-5.1$ echo -n "$F" | hexdump -C
00000000  5c 6e                                             |\n|
00000002
bash-5.1$ F=$'\n'
bash-5.1$ echo -n "$F" | hexdump -C
00000000  0a                                                |.|
00000001
bash-5.1$
```
