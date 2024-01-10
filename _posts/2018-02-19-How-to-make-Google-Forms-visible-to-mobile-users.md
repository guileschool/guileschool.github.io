---
layout: post
comments: true
title: 구글 설문지를 모바일에서도 잘 보이도록 Responsible 하게 만드는 법
author: mac.automator
date: 2018-02-19 14:24
tags: [자동제어,자동화,time-saver,리눅스,맥북,스마트홈,구글설문지,GoogleForms]
---

원문 http://guileschool.com/2018/02/19/How-to-make-Google-Forms-visible-to-mobile-users/

인용 https://www.quora.com/Ive-designed-a-survey-using-Google-Forms-but-it%E2%80%99s-way-too-wide-for-mobile-use-How-do-I-make-a-Google-form-responsive-on-a-mobile

모바일에서는 가로(Transverse) 보기 하시면 잘 보입니다 😄
[새 페이지로 열기](https://docs.google.com/forms/d/e/1FAIpQLSf0gYDNW-i6VPCe0XdcYL8GaJ0pmWk2z8dnUfPOgXmzDk448A/viewform)

<style>
@media (max-width: 767px) {
    iframe {
        max-width: calc(100vw + 40px) !important;   
        margin: -11px -25px;}
    .iframe-wrapper { 
        width:100vw; 
        overflow: hidden; 
        margin: 0 -15px;}  
/* you might not the margin property on the wrapper (or you might need to change it to suit your needs); in my case it's used to align the wrapper with the edge of the screen as my site has 15px padding, which isn't needed here because the form already has it's own padding   */
}
</style>

<div class="iframe-wrapper">
    <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSf0gYDNW-i6VPCe0XdcYL8GaJ0pmWk2z8dnUfPOgXmzDk448A/viewform?embedded=true" width="760" height="1800" frameborder="0" marginheight="0" marginwidth="0">Loading...  </iframe>
</div>

- 관련 HTML 소스  

```html
<style>
@media (max-width: 767px) {
    iframe {
        max-width: calc(100vw + 40px) !important;   
        margin: -11px -25px;}
    .iframe-wrapper { 
        width:100vw; 
        overflow: hidden; 
        margin: 0 -15px;}  
/* you might not the margin property on the wrapper (or you might need to change it to suit your needs); in my case it's used to align the wrapper with the edge of the screen as my site has 15px padding, which isn't needed here because the form already has it's own padding   */
}
</style>

<div class="iframe-wrapper">
    <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSf0gYDNW-i6VPCe0XdcYL8GaJ0pmWk2z8dnUfPOgXmzDk448A/viewform?embedded=true" width="760" height="1800" frameborder="0" marginheight="0" marginwidth="0">Loading...  </iframe>
</div>

```
