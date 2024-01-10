---
layout: post
comments: true
title: freertos 하드웨어 인터럽트 우선순위 정리
author: freertos
date: 2024-01-10 10:32
tags: [임베디드,RTOS,FREERTOS]
---

| **우선순위** | **인터럽트 유형**                | **설명**                                                     | **비고** |
| ------------ | -------------------------------- | :----------------------------------------------------------- | :------- |
| **Higher**   | **System Excepton Interrupts**   | hardfault(-1), NMI(-2), Reset(-3)                            |          |
| **0**        |                                  |                                                              |          |
|              | **NON-RTOS HW Interrupts**       |                                                              |          |
| **5**        | ────────────────                 | **configMAX_SYSCALL_INTERRUPT_PRIORITY(5)**<br />configLIBRARY_MAX_SYSCALL_INTERRUPT_PRIORITY 와 동일 |          |
|              | **RTOS awareness HW Interrupts** | 이 구간(PRIO 6~15)에서 발생하는 이 인터럽트들은 권리와 의무를 함께 가짐<br />**권리:**<br />1. taskENTER_CRITICAL(), taskEXIT_CRITICAL() 에 대해 인터럽트 활성화 비활성화 가능<br />2. 각 하드웨어 인터럽트 핸들러 함수의 마지막에서 portYIELD_FROM_ISR()을 호출함으로해서 하드리얼타임의 중요한 요건인 HW_ISR 내에서 선점이 일어날 수 있게 해줌<br /><br />**의무:**<br />인터럽트 핸들러에서 커널 함수를 호출하고 싶을 경우에는 반드시 xTaskResumeFromISR 와 같은 XXXXXX_FromISR() 형태의 커널 API 만 사용해야 한다 |          |
| **15**       | ────────────────                 | **configKERNEL_INTERRUPT_PRIORITY(15)**<br />configLIBRARY_LOWEST_INTERRUPT_PRIORITY 와 동일 |          |
|              |                                  |                                                              |          |
| **Lower**    |                                  |                                                              |          |
