---
layout: post
comments: true
title: 맥의 배쉬 버젼을 업그레이드 하는 법
author: mac.automator
date: 2018-01-11 10:30
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

원글 링크
><a href='http://clubmate.fi/upgrade-to-bash-4-in-mac-os-x/'>clubmate.fi
</a>
<!--more-->

현재 배쉬 버젼을 확인 ▼

```bash
admin☠  echo $BASH_VERSION
3.2.53(1)-release
```

배쉬 버젼 업그레이드 ▼

```bash
# Update homebrew and install bash
admin☠  brew update && brew install bash
# Add the new shell to the list of allowed shells
admin☠  sudo bash -c 'echo /usr/local/bin/bash >> /etc/shells'
# Change to the new shell
admin☠  chsh -s /usr/local/bin/bash 
```

위 명령을 입력한 후 리부트(rebooting)

배쉬 버젼을 확인 ▼

```bash
admin☠  echo $BASH_VERSION
4.4.12(1)-release
```
