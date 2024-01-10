---
layout: post
comments: true
title: 구글 번역기를 위한 PopClip Extension
author: mac.automator
date: 2018-02-15 16:55
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

원문 http://guileschool.com/2018/02/15/PopClip-Extension-for-google-translate/

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/0prZPq+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"></font></font></figcaption></figure>

### 구글 번역기 API란?
><a href='https://cloud.google.com/translate/'>공식홈페이지</a>
<!--more-->
<figure>
<img class="width-100-height-auto" src="https://d.pr/i/1X2TlE+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"></font></font></figcaption></figure>

Cloud Translation API는 최첨단 기술인 신경망 기계 번역을 이용하여 임의 문자열을 지원되는 언어로 번역할 수 있는 간단한 프로그래매틱 인터페이스를 제공합니다. Translation API는 응답성이 높으므로 출발어의 원본 텍스트를 도착어(예: 프랑스어에서 영어)로 빠르고 동적으로 번역하기 위해 웹사이트와 애플리케이션을 Translation API와 통합할 수 있습니다. 출발어를 알지 못하는 경우를 대비하여 언어 감지 기능도 제공됩니다. 여기에 사용되는 획기적인 기계 번역 기술은 지속적인 업데이트를 거치므로 번역의 질이 계속 향상되고 새로운 언어와 언어 조합이 추가됩니다
-출처: 구글클라우드-

### 팝클립이란?
><a href='http://pilotmoon.com/popclip/'>공식홈페이지</a>
<!--more-->
<figure>
<img class="width-100-height-auto" src="http://pilotmoon.com/popclip/images/Mainshot-en.png"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;"></font></font></figcaption></figure>

**PopClip** 은 Mac에서 마우스로 텍스트 를 선택할 때 나타납니다 . 검색 및 맞춤법 검사, 사전 및 100 개 이상의 작업을 즉시 복사하여 붙여 넣기하고 액세스하십시오

# translateGoogle
구글 번역기와 팝클립 기반의 다국어 번역을 위한 팝클립(PopClip) 확장 플러그인

### 특징
- 지원 가능한 언어는 26개 정도( **번역(지원) 가능한 언어** 참고 )
- DMG 파일 타입의 설치프로그램(translateGoogle.dmg)을 이용하거나
 수동설치(translateGoogle.popclipext)를 이용할 수 있슴.   
설치 방법은 **사전 준비사항** 와 **설치** 을 참고하세요

### 번역(지원) 가능한 언어

>한국어(ko)  
>영어(en)  
>아랍어(ar)  
>체코(cs)  
>덴마크어(da)  
>독일어(de)  
>그리스어(el)  
>스페인어(es)  
>핀란드어(fi)  
>프랑스어(fr)  
>히브리어(he)  
>헝가리어(hu)  
>이탈리아어(it)  
>일본어(ja)  
>노르웨이어(nb)  
>네덜란드어(nl)  
>노르웨이어(nn)  
>폴란드어(pl)  
>포르투갈어(pt)  
>러시아어(ru)  
>슬로바키아어(sk)  
>슬로베니아어(sl)  
>스웨덴어(sv)  
>터키어(tr)  
>중국어 간체(zh)  
>중국어 번체(zh)  

<!--more-->

### 설치환경
- 맥(혹은 맥북)
- 윈도우(x86)는 지원안함
- OSX 10.11+

### 구글 클라우드 서비스 가입
구글 계정이 있으면 별도의 조건없이 즉시 신청 가능 <a href='https://console.cloud.google.com/freetrial'>구글 클라우드 서비스 신청</a>
<!--more-->
[YOUTUBE](https://youtu.be/1yKyhHKjY0U)

무료 서비스(trial) 기간 만료 후 유료로 전환함

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/8trVCV+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 가입화면</font></font></figcaption></figure>

### 설치
**공통설치**를 먼저하고 난 후, **자동설치**(설치프로그램을 이용한 설치)을 이용하거나, 혹은 **수동설치**를 이용할 수 있다

### 공통 설치
공통 설치는 총 3가지로서 이미 <<`homebrew`, `wget`, `jsawk`, `popclip`>> 프로그램이 설치되어 있다면, 이 단계는 생략할 수 있다.

#### 1.Homebrew 설치
The missing package manager for macOS
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

for details here [Install Homebrew](https://brew.sh/index_ko.html)
<!--more-->

#### 2.wget 와 jsawk의 설치

```bash
$ brew install wget jsawk
```

#### 3.PopClip App 설치

><a href='http://pilotmoon.com/popclip/'>Official site
</a>
<!--more-->

### 자동 설치( 사전 설치 )

다운로드하세요 [here](https://d.pr/f/Nx6NOp+) <-- 자동설치용

[YOUTUBE](https://youtu.be/cwyXwt0L1nU)

1. 설치 패키지를 내려받으세요
2. 설치를 시작하세요 
3. 필수 프로그램(brew/wget/jsawk/popclip)들이 설치가 되어있고, 이 프로그램들에 특별한 문제가 없다면 설치를 계속 진행 할 수 있습니다
4. 만약 문제가 발생한다면 **각주**[^1] 을 참조하세요

### 수동 설치
 
다운로드하세요 [here](https://github.com/guileschool/translateGoogle/releases) <-- 수동설치용

[YOUTUBE](https://youtu.be/9oPiTzoA8r8)

소스 리뷰 [here](https://github.com/guileschool/translateGoogle/blob/master/translateGoogle.popclipext)

- `translateGoogle.popclipext` 파일의 파일명을 `translateGoogle.zip` 으로 변경한다

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/ZmDMW5+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 설치준비 화면</font></font></figcaption></figure>

- 해당 디렉토리(`translateGoogle.zip`)내의 파일중 `(1)translate_encode.sh` `(2)translate_decode.sh` `(3)Config.plist` 을 편집한다 

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/AXJatf+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 파일 수정 작업</font></font></figcaption></figure>

- 편집을 완료하고나면, 파일명(`translateGoogle.zip`)을 원래의 파일명(`translateGoogle.popclipext`)으로 다시 복원(수정)한다
- translateGoogle.popclipext 을 더블클릭하면 설치가 완료된다

- 구글 번역 서비스 키 정보의 입력

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/fln2mS+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 구글 번역 서비스 키 정보 입력</font></font></figcaption></figure>

- 이제부터 사용하면 된다

### 사용방법
단어나 문장을 **마우스**로 선택함과 동시에 **popclip** 팝업창이 뜨며, 이중 원하는 **번역** 지원 아이콘(버튼)을 클릭한다
<figure>
<img class="width-100-height-auto" src="https://d.pr/i/RTjdNm+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 구글 번역기 이용</font></font></figcaption></figure>

### 설치 이후의 언어 변경
사용하다가 번역언어 설정의 변경이 필요할 경우, 아래 2가지 방법 중 하나를 이용한다
- 방법1. 설치 프로그램을 이용해 플러그인을 다시 설치한다
- 방법2. translateGoogle 플러그인의 설치 경로로 이동한 후 해당 파일을 편집한다

▼ translateGoogle 플러그인의 설치 경로 
현재 사용자의 홈 디렉토리(폴더)내의 "Library/Application Support/PopClip/Extensions/translateGoogle.popclipext" 경로

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/35FdYy+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 팝클립확장 설치 폴더</font></font></figcaption></figure>

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/cpJTzG+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 터미널로 본 디렉토리 구조</font></font></figcaption></figure>

## 단축키를 쓰고 싶다면?
[키보드 마에스트로 프로그램](https://www.keyboardmaestro.com)이 반드시 필요합니다

[![YOUTUBE](http://img.youtube.com/vi/KxMeBvHhRmI/0.jpg)](https://youtu.be/KxMeBvHhRmI?t=0s)

▲ 키보드마에스트로 설치( YOUTUBE )

이 방법 말고 다른 방법의 지원을 원하신다면 글쎄요... 아직은 계획없습니다

[매크로파일 다운로드](https://d.pr/f/pKrww8+)
SHA256SUM
07b4353b414fcfd74c8aa785a877563cc908cbf0bf156bb17a0c1b30bac0fbd9  `Language Translator Macros.kmlibrary`
<!--more-->

[![YOUTUBE](http://img.youtube.com/vi/nDz1HVk8RKI/0.jpg)](https://youtu.be/nDz1HVk8RKI?t=0s)

▲ 매크로 데모( YOUTUBE )

#### 간단한 사용방법 
매크로파일을 다운로드 한 이후 해당 파일을 더블클릭하면 설치가 간단히 완료된다

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/gp678p+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 번역 매크로의 설치</font></font></figcaption></figure>


처음에 한번에 한하여 <kbd><⌘+⌃+⇧+`></kbd> 을 눌러서 번역기 기본 설정을 해 준다

[![YOUTUBE](http://img.youtube.com/vi/hiu1jZb2ABI/0.jpg)](https://youtu.be/hiu1jZb2ABIt=0s)

▲ 매크로 사용 방법( YOUTUBE )

원하는 문장이나 단어를 선택(SELECTION) 하고 KEY1 을 누르면 즉시 번역문으로 변경된다(replace)
원하는 문장이나 단어 바로 뒤에 커서를 위치시킨 상태에서 KEY2, KEY3, 혹은 KEY4 을 누르는 방식도 가능하다

KEY1은 선택한 부분을 번역

KEY2은 커서 바로 직전 단어 번역

KEY3은 컬럼1 부터 현재 커서 위치까지를 번역

KEY4은 전체 선택 번역

#### 단축키 CHEAT SHEET

| MAIN KEY | TITLE | DESCRIPTION | KEY1 | KEY2 | KEY3 | KEY4
| :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----:
| ` | Select Translator | 번역기 기본 설정 | <kbd><⌘+⌃+⇧+`></kbd> | None | None  | None
| NUM6 | Replacement | 기존 문장을 대치한다 | <kbd><⌘+6></kbd> | <kbd><⌥+⇧+6></kbd> | <kbd><⌘+⇧+6></kbd> | <kbd><⌘+⌃+⇧+6></kbd>
| NUM7 | Parentheses | 기존문장(번역문) | <kbd><⌘+7></kbd> | <kbd><⌥+⇧+7></kbd> | <kbd><⌘+⇧+7></kbd> | <kbd><⌘+⌃+⇧+7></kbd>
| NUM8 | Dash | 공백문자를 모두 '-' | <kbd><⌘+8></kbd> | <kbd><⌥+⇧+8></kbd> | <kbd><⌘+⇧+8></kbd> | <kbd><⌘+⌃+⇧+8></kbd>
| NUM9 | UnderScore | 공백문자를 모두 '_' | <kbd><⌘+9></kbd> | <kbd><⌥+⇧+9></kbd> | <kbd><⌘+⇧+9></kbd> | <kbd><⌘+⌃+⇧+9></kbd>
| NUM0 | Clipboard | 번역결과를 클립보드에 저장 | <kbd><⌘+0></kbd> | <kbd><⌥+⇧+0></kbd> | <kbd><⌘+⇧+0></kbd> | <kbd><⌘+⌃+⇧+0></kbd>
| - | Double_wildcard | 마크다운 볼드체 | <kbd><⌘+-></kbd> | <kbd><⌥+⇧+-></kbd> | <kbd><⌘+⇧+-></kbd> | <kbd><⌘+⌃+⇧+-></kbd>
| + | Backtick | 마크다운 인라인 | <kbd><⌘+=></kbd> | <kbd><⌥+⇧+=></kbd> | <kbd><⌘+⇧+=></kbd> | <kbd><⌘+⌃+⇧+=></kbd>

이 **translate_hotkey** 의 가장 큰 장점은 특정 편집기나 지정된 어플리케이션에서만 사용할 수 있지 않고, 어떤 프로그램이든지 함께 사용 가능하다는 점이다

## 도움이 필요하십니까 버그를 발견했나요?

[위키](https://github.com/guileschool/translateGoogle/wiki)를 참고하십시오. 문제가 발생하거나 궁금한 점이 있으면 
[문제 섹션](https://github.com/guileschool/translateGoogle/issues)에 게시하십시오.  시작하도록 도와 드리겠습니다

## 저작자 
Copyright © 2015 guileschool by Guile Hong (guileschool@gmail.com)

## LICENSE
이 소스는 MIT 라이센스 하에 배포됩니다. [LICENSE](https://github.com/guileschool/translateGoogle/blob/master/LICENSE) 을 참조

[^1]: 사전 설치(brew/wget/jsawk/popclip)가 미설치 혹은 부적절할 가능성이 높다. 각 프로그램이 시스템에 설치되어 있는지 확인한다. 이 매뉴얼이나 [유튜브](https://youtu.be/cwyXwt0L1nU)을 확인하고도 해결이 되지 않으면 [문제 섹션](https://github.com/guileschool/translateGoogle/issues)에 질문을 올리세요
