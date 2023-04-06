---
layout: post
comments: true
title: KM에서 홈폴더의 경로가 다른 쉘스크립트를 만족시키는 방법
author: mac.automator
date: 2018-02-14 10:10
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈,키보드마에스트로]
---

원문 http://guileschool.com/2018/02/14/How-to-satisfy-a-different-shell-script-in-the-Home-folder-at-KM/

인용: http://leancrew.com/all-this/2017/03/the-keyboard-maestro-scripting-environment/

원소스 멀티유즈. 한개의 소스를 여러대의 컴퓨터에서 동작시키기 위해선 다음과 같이 홈디렉토리 경로에 대한 독립성이 유지될 필요가 있다.

다음과 같은 두가지 경우, 홈디렉토리의 경로가 다르다(drdrang, realname)
>#!/Users/drdrang/anaconda/bin/python

>#!/Users/realname/anaconda/bin/python

공통으로 만족시킬 수 있는 스크립트를 작성해 보면 다음과 같다

```bash
#!/usr/bin/env -S -P${HOME}/anaconda/bin python
```

