---
layout: post
comments: true
title: 리눅스에서도 맥의 pbcopy 와 pbpaste 을 사용해 보자
author: mac.automator
date: 2018-12-01 17:51
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

Pbcopy 및 Pbpaste 명령은 Linux에서 사용할 수 없습니다. 그러나 Xclip을 사용하면 그 것을 할 수 있습니다

xclip 패키지 설치
```bash
$ sudo apt-get install xclip
```

~/.bashrc 파일을 편집
```bash
alias pbcopy='xclip -selection clipboard'
alias pbpaste='xclip -selection clipboard -o'
```

테스트
```bash
admin☠  echo Hello world | pbcopy
admin☠  pbpaste
Hello world
admin☠
```



