---
layout: post
comments: true
title: 맥에 위험한 앱(APP)을 강제로 설치하기 위한 조치
author: mac.automator
date: 2019-02-13 18:29
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

맥에 설치하려는 앱의 제목이 "LockedApp" 라고 가정

1순위(권장)
```bash
#For a certain application run in Terminal:
admin☠  sudo xattr -rd com.apple.quarantine /Applications/LockedApp.app
```

2순위(위의 방법이 안될때)
```bash
#To disable checks globally run in Terminal:
admin☠  sudo spctl --master-disable
```
