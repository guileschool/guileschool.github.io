---
layout: post
comments: true
title: 재귀적 호출을 가진 for loop의 활용법
author: mac.automator
date: 2017-10-10 07:12
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

특정 확장명을 가진 파일을 삭제하기 위해 반복적으로 디렉터리를 반복하는 방법

원글링크
><a href='https://stackoverflow.com/questions/4638874/how-to-loop-through-a-directory-recursively-to-delete-files-with-certain-extensi'>스택오버플로우
</a>

간단한 소스이니 여기에 첨부하고 별도의 설명은 없다 ▼

특정 파일을 삭제
```bash
recursiverm() {
  for d in *; do
    if [ -d "$d" ]; then
      (cd -- "$d" && recursiverm)
    fi
    rm -f *.pdf
    rm -f *.doc
  done
}

(cd /tmp; recursiverm)
```

특정 단어가 포함된 라인을 삭제
```bash
recursivedeline() {
   for d in *; do     
    if [ -d "$d" ]; then
           (cd -- "$d" && recursivedeline);
    fi;
    for file in *; do
        if [ -f "$file" ]; then
            ex +g/lib2450//Uart\.h/d -cwq "$file"
        fi
    done;
   done;
}
(cd /tmp; recursivedeline)
```

특정 단어를 치환
```bash
recursivereplace() {
   for d in *; do     
    if [ -d "$d" ]; then
           (cd -- "$d" && recursivereplace);
    fi;
    for file in *; do
        if [ -f "$file" ]; then
            ed -s "$file" <<< $',s/Windows(R)-compatible/POSIX-conform/g\nw'
        fi
    done;
   done;
}
(cd /tmp; recursivereplace)
```
