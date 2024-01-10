---
layout: post
comments: true
title: 'progress.sh를 사용하여 완료까지 소요 시간 예측'
author: mac.automator
date: 2017-10-08 11:24
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈]
---

컴퓨터상의 온갖 작업의 완료 예상 시간을 측정하는 스크립트

원글링크
><a href='http://sysadminsjourney.com/content/2008/12/15/estimate-time-completion-est/'>progress.sh를 사용하여 완료까지 소요 시간 예측</a>


### 1단계. 테스트 시나리오의 구성

터미널 창에 다음 명령을 입력한다 ▼

```bash
admin☠  echo "" > test.out; for i in `seq 1 600`; do echo "SUCCESS" >> test.out; echo "$i" >> test.out; sleep 3; done
admin☠

```

### 2단계. 시간 측정 스크립트의 실행

터미널 창에 다음 명령을 입력한다 ▼

```bash
admin☠  ./progress.sh 'grep -c SUCCESS test.out' 600
admin☠

```
매개변수 ARG1('grep -c SUCCESS test.out') 에는 예시처럼 측정하고자 하는 데이터(정수)
을 입력해주고 ARG2(600) 은 측정의 종료 조건(값)을 입력해 주면 된다.

이와 같이 하면 훌륭히? 시간 측정이 잘 된다

<p align="center">
  <img src="http://d.pr/i/C8cnlD/4BilWJtn+" width="1000" usemap>
</p> 

<!--more-->

소스코드(progress.sh) 인용

```bash
#!/bin/bash

#CMD="tail -n1 .progress | cut -d' ' -f1"
if [ -n "$1" ]; then
  CMD=$1
  if [ -n "$2" ]; then
    TOTAL=$2
    if [ ! $TOTAL -gt 0 ]; then
      echo "ARG2 should be an integer > 0."
      exit 1;
    fi
  else
    TOTAL=0
  fi
else 
  echo "ARG1 should be a command that generates an integer!"
  echo "ARG2 (optional) should be the end integer."
  exit 1;
fi

SLEEP=30
NOW=$(eval $CMD)
echo $NOW

if [ $NOW -eq $NOW 2> /dev/null ]; then
  if [ ! $NOW -ge 0 ]; then
    echo "Running of '$CMD' produced output that is not greater than or equal to 0.";
    exit 1;
  fi
else 
    echo "Running of '$CMD' produced output that is not an integer.";
    exit 1;
fi
COUNT=0
AVGTOTAL=0
ETA="???"
while [ true ]; do
  sleep $SLEEP
  LATER=$(eval $CMD)
  RECS=$(echo "scale=2; ($LATER - $NOW) / $SLEEP" | bc -l)
  NOW=$LATER
  let COUNT=$COUNT+1
  AVGTOTAL=$(echo "scale=2; $AVGTOTAL + $RECS" | bc -l)
  AVG=$(echo "scale=2; $AVGTOTAL/$COUNT" | bc -l)
  if [ $TOTAL -gt 0 ]; then
    PERCENT=$(echo "scale=2; $LATER / $TOTAL * 100" | bc -l)
    if [ "$AVG" != "0" ]; then
      ETA=$(echo "scale=2; mins= ($TOTAL - $LATER)/ $AVG /60; if ( mins > 60 ) { print mins/60; print \" hrs\" } else {print mins;print \" mins\"}" | bc -l)
    fi
    echo -e "Current=$RECS/sec\tTotalAvg=$AVG/sec\tTotal=$LATER/$TOTAL $PERCENT%\t$ETA left"
  else
    echo -e "Current=$RECS/sec\tTotalAvg=$AVG/sec\tTotal=$LATER"
  fi
done

```
