---
layout: post
comments: true
title: 애플스크립트가 없는 맥은 비싼 유닉스 머신일 뿐이다
author: mac.automator
date: 2018-02-13 13:07
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈,애플스크립트]
---

원문 http://guileschool.com/2018/02/13/Mac-without-an-Applescript-is-an-expensive-Unix-machine/

지난 2016년 가을, 자동화 기술을 사랑하는 맥유저들은 충격적인 소식을 듣게 되었다
애플에서 지난 20년간 근무해 온 애플 자동화 기술 프로덕트 매니저가 해고 되었다는 것이다

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/6Hdt7h+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 살소고이안</font></font></figcaption></figure>

이에 커뮤니티에서는 이에 대해 우려의 말들이 쏟아져 나왔다.
다음은 그 주요 글들의 번역본(기계번역)이다

[글1](https://www.change.org/p/apple-keep-mac-user-automation-such-as-applescript-automator-in-mac-os-x/c?source_location=petition_show
) [글2](http://tidbits.com/article/17004) [글3](http://tidbits.com/article/17127) [글4](https://www.macstories.net/stories/app-extensions-are-not-a-replacement-for-user-automation/
)
 <!--more-->
 
스크립팅 언어는 컴파일 된 언어가 아닙니다. Swift와 Applescript는 자신이하는 일과 달성하고자하는 목표에서 별개의 세상입니다.
Swift는 처음부터 응용 프로그램을 작성하기위한 것입니다.
**Applescript는 응용 프로그램과 상호 작용하여 수행하는 작업을 자동화하고 여러 응용 프로그램의 기능을 사용하여 어떤 목표를 수행하는 접착제 역할을합니다**
Swift에서도 이 코드를 작성할 수는 있지만 훨씬 많은 코드가 될 것이며 소프트웨어 프로그래머가되어야합니다. 만약 당신이 소프트웨어 프로그래머라면, 스위프트는 애플 스크립트의 대신 할 수도 있고 그렇지 않으면 "아니오"는 아닙니다

와우. 이것이 AppleScript에 대해 무엇을 의미하는지 확신 할 수 없습니다. 내 스튜디오에서 엄청난 수의 작업을 자동화하기 위해 AppleScript를 사용합니다. 나는 주요 기업에서 사진 교정 부서를 운영하고 AppleScript가 없으면 거의 생산적이지 않을 것입니다. Applescript는 오류를 유발할 수있는 작업을 자동화하고 결과적으로 줄이거 나 제거 할 수 있기 때문에 품질을 보장합니다. 예를 들어 우리가 작업하는 각 이미지에 대해 레이어 된 Photoshop 파일을 저장하는 동안 파일을 자동으로 CMYK로 변환하고 올바른 이름으로 적절한 위치에 저장하는 "출력"스크립트도 실행합니다. 이 기능이 없으면 내 retouchers가 지속적으로 우리의 작업 흐름에 실수를 범할 것이라고 확신합니다.

또한 Applescript와 Automator를 산발적으로 사용했지만, 필요할 때 필요할 것입니다. 지금은 Indigo 홈 자동화 서버에 연결된 스크립트가 있습니다. 내 세탁기와 냉장고의 누수 감지기가 인디고로 신호를 보내면 문자 메시지와 아내가 메시지를 사용하는 스크립트가 실행됩니다. 이것은 Mac Mini에 있습니다. 차고 문이 위아래로있을 때도 알려주는 비슷한 스크립트가 있습니다. 반쯤 운전하면 효과적이며 닫은 경우에는 기억이 안납니다. Xserve가 장비실의 온도를 모니터링하고 난방이 과열되면 텍스트를 보낼 수있는 오래된 작업에서 비슷한 설정을했습니다. 

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/ZBqtE5+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 맥 오토메이터(Mac Automator)</font></font></figcaption></figure>


Apple이 언젠가 Applescript와 Automator를 제거한다면 나는 기술을 제 3 자에게 팔아서 계속 기능을 유지할 수 있을지 의아하게 생각합니다. 사람들은 항상 이것이 Windows와의 차별화 요소라고 말했습니다. 분명히 내가 "Mac을" 사람들에게 몇 번이나 말할 수 있었습니다

나에게있어, **프로그래머가 아닌 사람들이 응용 프로그램을 함께 묶는 방법 인 AppleScript는 아마 macOS의 가장 중요한 차별화 요소 일 것입니다**. 제 첫 Quadra 800부터 애플에 충실 했습니다만, 애플 스크립트를 포기한다면 윈도우나 일반 UNIX로 옮길 것입니다.

Automator는 내가 가장 좋아하는 유틸리티 앱 중 하나입니다. 단지 제 1 자와 제 3 자의 앱이 어떻게 협력 할 수 있는지는 순수한 마법입니다. 예를 들어, Finder에서 300 개의 스크린 샷을 복제 / 이름을 변경하고, Pixelmator로 보내어 자르기를 한 다음, 전송하여 내 서버에 업로드 할 수 있습니다. 수작업으로 솔직하게 목에 통증을 느낀다는 것은 솔직히 말해서, 모든 애플 리케이션이 나를 위해 내 작업을 완료하기 위해 함께 작동하도록하는 마술에 불과합니다

나는 수년에 걸쳐 자동화 된 작업을 수행했습니다. 내가 좋아하는,하지만 그 인상적, 1400 + 파일을 Excel 에서 웹 도움말 시스템으로 변환했다. 스크립트 반나절과 약 1 시간의 런타임으로 모든 것이 완료되었습니다.
그 점이 중요합니다. 작업을 자동화 할 수 없다면 컴퓨터가 아닙니다. AppleScript를 좋아하지는 않지만 Apple 이벤트를 만드는 것이 진정으로 큰 혁신이라고 생각합니다.
Swift는 무시 무시한 해결 방법에 의거하지 않고 Apple 이벤트와 직접 작업 할 수있는 방법을 제공 할 것입니다. 빠를수록 좋다.

AppleScript를 주로 InDesign 및 Illustrator 를 자동화하는 데 사용 하고 AppleScript가 JavaScript보다 큰 이점은 단일 스크립트에서 여러 응용 프로그램을 함께 묶을 수 있다는 것입니다. Excel 스프레드 시트의 데이터는 BBEdit 에서 정리 된 다음 최종적으로 InDesign 문서에 배치 된 Illustrator에서 그래프를 만드는 데 사용할 수 있습니다

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/EB0y3U+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 애플스크립트 디버거</font></font></figcaption></figure>

(AppleScript 편집기 / 디버거)의 개발자로서 제 업무에 자동화 된 산이 있습니다. Script Debugger를 컴파일하고 버그 추적기에서 릴리스 노트를 수집하며 소프트웨어 버전 관리를 관리하고 소프트웨어 업로드를 수행하는 자동화 기능을 구축했습니다. 한 사람 샵으로서 나는 신속하고 올바르게 수행해야 할 일이 필요합니다. 나는 이것을 손으로했을 때 항상 오류가있었습니다. 버그 리포트와 고객 지원 이메일을 다양한 방법으로 처리하는 버그 추적 자동화가 있습니다. 이메일 마케팅 자동화가 있습니다. 목록은 계속 켜져 있습니다. 자동화는 광산과 같은 작은 조직이하는 일을 성취 할 수있게합니다.
개인적 차원에서 나는 일상 생활에 많은 자동화 기능을 제공합니다. 예를 들어, 서적, CD 및 DVD를 빌리면 내 지역 도서관에서 전자 메일 확인을 전송합니다. 나는이 이메일을 처리하고 각 항목이 언제 다시 라이브러리로 돌아갈 지에 대한 알림을 생성하는 AppleScript를 가지고 있습니다.

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/obdWoi+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 전자출판</font></font></figcaption></figure>

Joern Dyck - 저는 비디오 스튜디오를 운영하고 있습니다. 우리는 라이브 쇼를 제작합니다. 녹화 된 쇼는 나중에 당사 웹 사이트에서 다운로드 할 수 있습니다. AppleScript는 하루 동안 쇼를 제작 / 방송 할 수 있고 밤에는 AppleScript로 편집 및 업로드를 처리 할 수 있기 때문에 절대적으로 필요합니다. 우리가 다음날 아침에 일하기 위해 돌아 왔을 때, 우리는 이미 처리, 확인, 업로드 및 보관 된 모든 것을 찾습니다. 그것은 마술입니다. 다음은 작동 방식입니다.
우리의 라이브 쇼는 3 시간 또는 4 시간의 지속 시간을 가지고 있습니다. 쇼가 끝난 후, 녹음 내용을 더 작은 부분으로 자릅니다. 이것은 우리가 많은 양의 데이터를 가지고 있음을 의미합니다. 이 때문에 후반 작업에는 많은 대기 (예 : 서버로 내보내기 / 압축 및 업로드)가 필요합니다.
이것은 야간에 가장 잘 할 수있는 일입니다.

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/Q33lWH+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 애플스크립트 편집기</font></font></figcaption></figure>


Final Cut Pro X는 데이터베이스에서 생성 된 XML 파일을 사용하여 자동화 할 수 있습니다. 데이터베이스에는 비디오 클립에 대한 모든 정보 (제목, 설명, 포스터 이미지 및 기타 많은 것들)가 있습니다. 그 결과 압축 된 비디오 파일이 폴더에서 대기합니다.
AppleScript는이 폴더에서 새 파일을 감시합니다. 새로운 파일이있을 때 AppleScript는 비디오를 몇 가지 추가 속성으로 제공하기 위해 몇 가지 추가 응용 프로그램을 사용합니다 (Final Cut Pro는 원하는 모든 작업을 수행 할 수 없기 때문입니다).
그런 다음 AppleScript는 비디오를 마스터 서버에 업로드합니다. 대용량 파일 (일부는 7 ~ 10GB)을 사용하면 성공이 보장되지 않기 때문에 사실 복잡한 프로세스입니다. AppleScript는 업로드가 성공적으로 완료되었는지 확인합니다. 그렇지 않은 경우 업로드를 반복합니다. 마지막으로 원하는 것은 10GB의 파일이 업로드되지 않았다는 것을 확인하기 위해 다음 날 아침에 다시 작동하도록하는 것입니다. 각 동영상 (소형, 중형, 대형)의 버전이 다르며 다른 프로그램 AppleScript는 지능적으로 올바른 폴더를 선택합니다.
그런 다음 AppleScript는 비디오를 로컬 아카이브에 저장하고 데이터베이스에 항목을 만듭니다. 우리가 일하러 돌아 오면 모든 것이 정리되고 다음 공연을 준비합니다. 무엇인가가 실패하면 DesktopEdit 문서를 추가 정보와 함께 넣을 수 있습니다. 또는 문제가되는 파일에 빨간색으로 레이블을 지정할 수 있습니다. 또는 책임자에게 전자 메일을 보낼 수 있습니다.

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/mYAi6I+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 파이널컷프로</font></font></figcaption></figure>


고객은 우리가 밤낮으로 일한다고 생각할 수도 있습니다. 우리는 다음날 아침 10 GB의 편집 된 비디오를 어떻게 제공 할 수 있습니까? 진실은 우리가 밤낮으로 일하는 팀을 가질 여력이 없다는 것입니다. 그리고 그 일은 지루하고, 반복적이며, 기다리는 시간이 길기 때문에 그렇게하는 것이 어리석은 일입니다. 다양한 응용 프로그램을 사용하는 자동화 된 워크 플로에 이상적인 기능입니다.
우리는 애플을 우리 같은 작은 팀이 대기업 만 할 수있게하는 회사로보고 있습니다. AppleScript가 바로 그 것입니다. 학습 곡선이 있지만 간단하게 시작할 수 있습니다. 일단 실행되면 믿을 수 없을 정도로 시원하고 생산적입니다. 애플은 그 이상을해야한다.
우리 시스템의 가장 중요한 부분은 행동 자체를 유발할 수 있다는 것입니다 (예 : 매분 확인하거나 폴더 모니터링). 의사 결정 (if, else) 및 다른 응용 프로그램 사용. **스위프트에서 뭔가를 프로그래밍하는 것은 우리에게는 선택 사항이 아닙니다. 우리는 소프트웨어 개발자가 아닙니다. 우리는 조리법과 비슷한 방식으로 쉽게 변형 될 수있는 무언가가 필요합니다.**
한 가지 더 예 : 라이브 쇼 중에 12 개의 Mac을 사용합니다. 각 쇼마다 다른 설정이 필요합니다. Mac을 설정하려면 1 시간이 걸립니다. AppleScript는 네트워크에서 Mac을 제어 할 수 있기 때문에이를 AppleScript로 자동화했습니다. AppleScript는 우리가 제작하고자하는 쇼를 요청하고 모든 것을 설정합니다. 한 번의 클릭만으로 모든 것을 준비 할 수 있습니다.

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/jsewjU+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 파이썬</font></font></figcaption></figure>


Eric Geoffroy - **AppleScript는 이 모든 것을 지배하는 하나의 고리입니다. AppleScript로 Finder, JavaScript, Python 및 bash를 제어 할 수 있습니다. 많은 자동화 솔루션은 다양한 도구 상자를 사용합니다. 연결되지 않은 스크립트 대신 AppleScript를 사용하여 이러한 프로그래밍 언어 및 다른 프로그래밍 언어에서 데이터를 가져와 하나의 마스터 스크립트에서 제어 할 수 있습니다.
Windows, Linux 및 iOS에는 AppleScript와 같은 기능이 없습니다. Mac이 할 수있는 몇 가지 독특한 기능 중 하나입니다. Windows는 특히 Mac을 특별하게 만드는 데 사용 된 모든 것을 복사했습니다.
자동화 된 솔루션의 시간 절약은 엄청납니다**. 나는 2-6 시간이 걸리고 인간의 실수를 야기하는 기존의 수작업 프로세스를 측정했다. 이러한 동일한 작업이 20 분으로 단축되었습니다. 어떤 경우에는 비율이 30 : 1입니다.
저는 회사에서 우리가 PC로 전환하게하여 워크 플로우와 생산성을 파괴하게 될까봐 걱정했습니다. 나는 수년간 마이크로 소프트 윈도와 싸웠다. 이제 나는 애플이 무엇을 할까 두려워한다.

<figure>
<img class="width-100-height-auto" src="https://d.pr/i/0f6Nam+"><figcaption><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">▲ 맥북프로</font></font></figcaption></figure>


나는 AS와 오토메이션에 의존적인 어플리케이션를 가지고 있다. 이러한 애플리케이션은 다른 소프트웨어에서 찾을 수 없는 솔루션을 제공합니다. AS는 기존 소프트웨어를 결합하여 OS와 기존 소프트웨어를 더 많이 만드는 데 사용됩니다. AS는 내가 계속 맥오에스와 애플에 의지하게 해준다.

Apple에서 AppleScript와 Automator를 포기하면 나는 미련없이 Windows및 AutoHotkey로 전환할 것이다. 듣고 있어요, 팀?

애플스크립트가 없는 매킨토시는 아주 비싼 하드웨어를 가진 또 하나의 UNIX 맛이 될 것이다.

나는 프로 유저이고 20여년간 Mac을 이용해 왔다. AppleScript는 내 삶을 더욱 편안하게 해 주었다. 계속 개발해 주세요.

자동화는 매우 중요한 기능입니다. 그것은 혼자서 해결할 수 없는 문제들을 해결한다. 나는 그것이 필요하다.

나는 Mac이 Applescript, Xcode, Automator와 함께 큰 이점을 가지고 있다고 믿는다.