---
layout: post
comments: true
title: Synchronous 방식으로 동작할 수 있는 애플스크립트의 do shell script
author: mac.automator
date: 2018-02-06 10:40
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

원문 http://guileschool.com/2018/02/06/do-shell-script-of-Apple-Script-that-can-operate-in-Synchronous/

### 초간단 설명
쉘 스크립트의 리턴값을 확인할 필요가 없는 경우라도 리턴값을 받으려고 시도한다
결과를 받기위해 스크립트는 대기하고 기다릴 수밖에 없다

```applescript
set NOT_INSTALL_PACKAGE to do shell script "echo $(find /usr -iname pip3 2>/dev/null | grep -rni pip3 >/dev/null 2>&1; echo $?)"
code
```