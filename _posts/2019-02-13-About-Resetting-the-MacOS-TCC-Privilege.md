---
layout: post
comments: true
title: MacOS TCC 권한 재설정에 관한 이야기
author: mac.automator
date: 2019-02-13 18:38
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

아래는 원글의 일부만 발췌
자세한 내용은 **MarsEdit 4** 라는 앱을 개발하기도 한 전직 애플개발자 **Daniel Jalkut**의 글을 참조
https://bitsplitting.org/2018/07/11/reauthorizing-automation-in-mojave/

제목: 모하비의 자동화 재 인증
2018 년 7 월 11 일
macOS Mojave 베타에는 자동화 된 작업을 수행 할 수있는 응용 프로그램에 대한 사용자 제어가 크게 향상되었습니다. Mac에서 자동화에 관해 이야기 할 때 AppleScript 또는 Automator에 대해 일반적으로 생각하지만 더 넓은 관점의 자동화는 한 응용 프로그램에서 다른 응용 프로그램으로의 모든 통신으로 볼 수 있습니다.

이러한 자동화의 유비쿼터스 한 예가 "Finder에서 공개"유형 기능의 보급입니다. 예를 들어 iTunes에서 노래 파일을 마우스 오른쪽 단추로 클릭하면 상황에 맞는 메뉴의 옵션을 사용하여 Finder에서 파일을 표시 할 수 있습니다. 이것은 iTunes에서 Finder로 "Apple Event"를 전송함으로써 수행되는 매우 기본적인 자동화입니다.

macOS Mojave 베타 버전에서는 응용 프로그램에서 이러한 명령을 호출하면 사용자 권한을 요청하는 패널로 이어질 가능성이 높습니다. 사용되는 용어는 다음과 같습니다.

"WhateverApp"가 응용 프로그램 "Finder"를 제어하려고합니다.

... 중략

TCC 권한 재설정
나는 과거의 경험을 통해 자신의 애플 리케이션에서 연락처 권한을 테스트했다는 것을 알았습니다. 애플은 권한 재설정을위한 메커니즘을 지원합니다. 안타깝게도 이전과 비교해 보았던 애플리케이션의 권한 설정을 변경하려면 특정 서비스를 사용하는 모든 앱의 모든 권한을 완전히 제거해야합니다.

애플이벤트의 경우 :

```bash
tccutil reset AppleEvents
```

파인더의 경우 :

```bash
tccutil reset Finder
```
