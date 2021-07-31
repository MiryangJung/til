---
layout: default
title: Note-fastcampus-reactwithshoppingmall
parent: React
---

# 패스트캠퍼스 React로 쇼핑몰 만들기 강의노트
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

>  [패스트캠퍼스 한 번에 끝내는 프론트엔드 개발 초격차 패키지 Online. - Part 10. React 로 쇼핑몰 만들기](https://fastcampus.co.kr/dev_online_frontend)



## CH 1. React Getting Started

### Client Side Rendering (CSR)  

1. 서버에서 html 전달받음
2. html 안의 js 다운로드
3. 리액트 웹앱 실행
4. 화면 그려짐

- js가 전부 다운되어 리액트가 실행되기 전까지는 화면이 보이지 않음.

### Server Side Rendering (SSR)

1. 렌더링 된 html 전달받음
2. 화면 그려짐, html 안의 js 다운로드
3. 리액트 웹앱 실행
4. 페이지 작동

- js가 전부 다운되지 않아도, 화면은 보이지만 유저가 사용할 수 없음.

### 핵심 모듈 2개

**ReactDOM**  
- 리액트 컴포넌트를 HTMLElement에 연결

**react**  
- 리액트 컴포넌트 만들기


## Ch 2. React Component

### Class 컴포넌트

```javascript
class ClassComponent extends React.Component{
    render(){
        return <div>Hello</div>
    }
}
```

### Function 컴포넌트

```javascript
function FunctionComponent(){
    return <div>Hello</div>
}
```

### React.createElement

```javascript
React.createElement(
    type, // 태그 이름 문자열 | 리액트 컴포넌트 | React.Fragment
    [props], // 리액트 컴포넌트에 넣어주는 데이터 객체
    [...children] // 자식 요소들
)
```

### babel

jsx 문법으로 작성된 코드를 순수한 js로 컴파일해준다.

### jsx

- 최상위 요소는 하나
- js 표현식 `{}`
- if문은 사용할 수 없음
    - 삼항 연산자 혹은 논리 연산자 사용
- class 대신 className 사용