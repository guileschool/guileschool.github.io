---
layout: post
comments: true
title: 사인파(sinewave) 음향 효과 만들기
author: mac.automator
date: 2019-02-13 18:11
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

원하는 시간 길이(1.0sec), 음량(13/18/20dB)의 사운드를 생성
```bash
  admin☠ ffmpeg -f lavfi -i "sine=frequency=10:duration=1.0" -t 1.0 ~/Desktop/wav/sine10Hz.wav
  admin☠ ffmpeg -i sine10Hz.wav -af "volume=20dB" -t 1.0 sine10Hz-20db.mp3
  admin☠ ffmpeg -i sine10Hz.wav -af "volume=18dB" -t 1.0 sine10Hz-18db.mp3
  admin☠ ffmpeg -i sine10Hz.wav -af "volume=13dB" -t 1.0 sine10Hz-13db.mp3
```


