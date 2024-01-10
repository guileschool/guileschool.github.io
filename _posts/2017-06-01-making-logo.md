---
layout: post
comments: true
title: '가일스쿨 로고 만들기'
author: mac.automator
date: 2017-06-01 18:34
tags: [TEXT TO IMAGE,IMAGEMAGICK,AUTOMATOR,MACBOOK,SHELL,BASH]
---

## 문자열을 이미지 파일로 변환해 준다

[ImageMagick 설치하기](https://rorlab.gitbooks.io/railsguidebook/content/appendices/imagemagick.html)
<!--more-->

```bash
$ convert -size 99x17 xc:none -font 나눔고딕 -pointsize 18  -fill black -gravity center -draw "text 0,0 'GuileSchool'" tech_logo.png

$ convert -size 198x34 xc:none -font 나눔고딕 -pointsize 34  -fill black -gravity center -draw "text 0,0 'GuileSchool'" tech_logo@2x.png

$ convert -size 297x51 xc:none -font 나눔고딕 -pointsize 52  -fill black -gravity center -draw "text 0,0 'GuileSchool'" tech_logo@3x.png
```

### 변환결과

<p align="center">
  <img src="http://d.pr/i/a7MJlS/B36rfRWF+" width="1000" usemap>
</p> 

