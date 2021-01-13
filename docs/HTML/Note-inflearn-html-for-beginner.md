---
layout: default
title: Note.inflearn-html-for-beginners
parent: HTML
---

# 초보자를 위한 HTML 기초 강의노트

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

---

> [인프런 - 초보자를 위한 HTML 기초](https://www.inflearn.com/course/html-%ED%91%9C%EC%A4%80-%EA%B8%B0%EC%B4%88)

## HTML 이란?

- Hypertext Markup Language
- Markup Language : 태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어
- HTML 표준은 관련 API 포함
- HTML 5 는 공식적으로 폐기된 상태
- HTML LIVING STANDARD 가 표준
- 웹의 근간
- 브라우저가 공식적으로 지원하는 언어 4종류
  - HTML, CSS, JS, WASM

## 웹 브라우저 전쟁과 웹 표준

- 브라우저 전쟁
  - IE 와 Netscape Navigator 브라우저 사이에 있었던 점유율 전쟁
- 웹 표준
  - 웹 기술 스펙을 작성하여 모두가 기대한대로 작성하면 기대한 결과를 얻게 해주는 것

## 웹 콘텐츠 접근성

- 접근성은 반드시 장애인을 대상으로 하는 것은 아니다.
- W3C 에서 관리
- KWCAG
  - 인식의 용이성
  - 운용의 용이성
  - 이해의 용이성
  - 견고성

## 브라우저와 브라우저 엔진

- 웹 브라우저
  - HTML, CSS, JS, WASM에 이르는 다양한 언어를 해석
  - 해석한 결과를 바탕으로 렌더링
- 웹 브라우저 구성
  - 브라우저 엔진(렌더링 엔진)
  - 자바스크립트 엔진0
  - 통신 모듈
- 브라우저 엔진
  - 브라우저가 동작하는 데 필요한 기반 기술을 모두 포함하는 엔진
  - 브라우저 엔진에 따라서 동작 방식이 거의 유사하다.
  - 종류
    - Blink Engine(Chrome, Opera, Samsung Internet, MS Edge, Whale, Brave)
    - WebKit Engine(Safari)
    - Servo Engine(Firefox)

## 표준화기구

- W3C
  - CSS, MathML, EmotionML, Payment...
- WICG
  - W3C의 산하 커뮤니티 그룹
  - 새로운 기술 표준을 제안
- WHATWG
  - HTML Living Standard, DOM, Encoding...
  - HTML5 스펙이 원래 W3C에 있다가, WHATWG와 통합
- ECMA International
  - ECMAScript
  - JSON
- TC 39
  - JavaScript 표준을 관리하는 그룹
- IETF
  - 인터넷의 운영, 관리, 개발에 대해 협의하고 기술 프로토콜 만들어 표준 부여
  - HTTP, WebSocket...
- ISO
  - 다양한 분야의 표준을 정의하고 관리

## HTML Living Standard

- [html.spec.whatwg.org/multipage/](https://html.spec.whatwg.org/multipage/)

## 기본 HTML 템플릿

```html
<!DOCTYPE html> <!-- HTML 버전 명시 -->
<html lang="ko">
    <head>
        <!-- Document Metadata -->
        <!-- 다른 문서나 다른 머신에게 이 문서에 대한 정보를 제공하는 데이터 -->
        <title>Document Title</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="initial-scale=1, width=device-width">
    </head>
    <body>
        <!-- 이 문서의 핵심 내용 -->
        <!-- 기본적으로 유저의 눈에 보임 -->
    </body>
</html>
```

## DOCTYPE

- 문서의 타입과 버전을 나타낼 때 사용
- DOCTYPE을 선언하지 않으면, Quirks mode 라는 하위 호환성 모드로 진입

## HTML Content model

- 특정한 요소가 어떤 콘텐츠를 나타내는 지 보여주기 위한 모델
- Metadata Content
  - 문서에 대한 정보를 다른 문서나 bot에게 전달하는 요소들
  - link, meta, scirpt, noscript,style, title
- Flow Content
  - 문서의 body 내에 포함되는 대부분의 요소들
- Sectioning content
  - HTML의 구역을 나눌 때, heading과 footer의 범위를 지정할 때 사용하는 콘텐츠 모델
  - article, aside, nav, section
- Heading content
  - section의 제목을 나타낼 때 사용하는 콘텐츠 모델
  - h1,h2,h3,h4,h5,h6,hgroup
- Phrasing content
  - HTML 문서 내에서 text를 사용하는 모든 콘텐츠 모델
  - text처럼 취급되는 모든 요소
- Embedded content
  - HTML 문서 내에서 다른 리소스(이미지, 비디오, 오디오)를 불러오는 콘텐츠
  - audio, video, img, picture, svg, math, iframe, canvas
- Interactive content
  - 유저와 상호작용이 발생하는 모든 요소
  - a (href), audio(controls), video(controls), input, label, button, select, textarea, img(usemap)
- Palpable content
  - 콘텐츠가 자식 노드를 가지지 않거나 숨김 상태인 경우
- Script-supporting content
  - 스크립트를 지원하기 위해 사용하는 요소
  - script, template
- Transparent content model
  - 어떤 콘텐츠에 속하느냐에 따라 콘텐츠 모델이 달라지는 걸 의미
  -  