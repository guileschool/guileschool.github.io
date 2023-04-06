---
layout: post
comments: true
title: '맥 앱 아이콘(icns) 제작방법'
author: mac.automator
date: 2017-07-02 12:47
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

맥 어플리케이션 제작시 필요한 아이콘(icns) 제작 단계에 대해서 적어본다

<p align="center">
  <img src="http://d.pr/i/yaJwXH/49Of7aFU+" width="1000" usemap>
</p> 

<!--more-->


### 1단계. 이미지를 준비한다
이미지는 정사각형이어야하며 완전한 아이콘 세트를 제공하는 것이 좋다. 하지만 꼭 완전한 세트를 가질 필요는 없다. 시스템이 어플에서 제공하지 않는 아이콘은 크기와 해상도를 추측하여 표현할 것이다.

완전한 세트는 다음과 같이 준비한다

>`<TIP>` 고해상도 이미지를 1개 준비한 후 나머지 이미지들은 축소(resizing)하여 만들면 된다. 😀 

```
icon_16x16.png
icon_16x16@2x.png
icon_32x32.png
icon_32x32@2x.png
icon_128x128.png
icon_128x128@2x.png
icon_256x256.png
icon_256x256@2x.png
icon_512x512.png
icon_512x512@2x.png
```

### 2단계. 이미지를 아이콘으로 변환한다
>iconutil -c icns `<iconset 파일 이름>`

터미널 창에 다음 명령을 입력한다 ▼

```bash
admin☠  iconutil -c icns icon.iconset
admin☠

```

이와 같이 하면 훌륭히? 아이콘(icns)이 잘 만들어 진다

>xcode 4.4 이후부터는 이와같은 과정 필요없이 아이콘 이미지를 준비한 후 폴더를 드래그앤드랍으로 프로젝트에 넣은 후 빌드(build)하면 자동으로 icns 아이콘이 생성된다

<p align="center">
  <img src="http://d.pr/i/XIQalp/4yGwdmQt+" width="1000" usemap>
</p> 

### 추가. icns아이콘을 이미지로 역변환하려면
>iconutil -c iconset `<icns 파일 이름>`

터미널 창에 다음 명령을 입력한다 ▼

```bash
admin☠  iconutil -c iconset icon.icns
admin☠

```
