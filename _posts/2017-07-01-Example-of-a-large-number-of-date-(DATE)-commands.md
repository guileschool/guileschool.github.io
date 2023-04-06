---
layout: post
comments: true
title: '날짜(DATE) 명령어의 다양한 입력 예'
author: mac.automator
date: 2017-07-01 16:37
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

현재 날짜와 시간을 확인하는 명령어의 다양한 예를 확인해 보았다

<p align="center">
  <img src="http://d.pr/i/uEDUe8/3DIRaMSx+" width="1000" usemap>
</p> 
<!--more-->

### 4자리 연도 표시
```bash
admin☠  date +"%Y-%m-%d"
2017-07-01
```

### 4자리연도+시간 표시
```bash
admin☠  date +"%Y-%m-%d %r"
2017-07-01 04:58:21 PM
```

### 시간을 HH : MM 형식으로 표시 
```bash
admin☠  date +"%Y-%m-%d %H:%M"
2017-07-01 17:00
```

### 요일 표시 
```bash
admin☠  date +"%Y-%m-%d %H:%M %A"
2017-07-01 17:01 토요일
```

### 포맷형 표시 
```bash
admin☠  date "+DATE: %Y-%m-%d%nTIME: %H:%M:%S"
DATE: 2017-07-01
TIME: 17:03:15
```

### 현재 시간을 실시간으로 출력
```bash
while true; do TIME=$(date "+DATE: %Y-%m-%d %H:%M:%S"); echo -ne "${TIME}\r"; done
```