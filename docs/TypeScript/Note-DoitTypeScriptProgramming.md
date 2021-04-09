---
layout: default
title: ES5
parent: TypeScript
---

# Do it! 타입스크립트 프로그래밍 노트
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
   {:toc}

---

## 1장
### 개발 환경 구성

1. __scoop__ (윈도우 커맨드 기반의 패키지 관리자) 프로그램 설치
파워쉘에서 입력  
```
Set-ExecutionPolicy RemoteSigned -scope CurrentUser  
$env:Scoop='C:\Scoop'
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
scoop install aria2
```

2. VSCode 설치
3. node.js 설치  
```
scoop install nodejs-lts
node -v
```

4. 타입스크립트 컴파일러 설치  
```
npm i -g typescript
tsc -v
```

5. ts-node 설치  
```
npm i -g ts-node
```

## 2장
### 프로젝트 만들기

node.js 프로젝트를 만든 다음, 개발 언어를 ts로 설정하는 방식

```
npm init
```

`package.json` 이 생성
   - 패키지 관리 파일
   - 프로젝트 정보와 관련 패키지가 기록


필요 패키지를 개발에 필요한 패키지로 설치

```
npm i -D typescript ts-node @types/node

---
  "devDependencies": {
    "@types/node": "^14.14.37",
    "ts-node": "^9.1.1",
    "typescript": "^4.2.4"
  }
```

`tsconfig.json` 타입스크립트 컴파일러 설정 파일

```
tsc --init
```

타입스크립트 소스코드를 자바스크립트 코드로 변환해 node 로 실행하기 위해 package.json 수정

```
  "main": "src/index.js",
  "scripts": {
    "dev":"ts-node src",
    "build":"tsc && node dist"
  },...
```

- dev : 개발 중 index.ts 파일을 실행하는 용도
- build : 프로그램을 배포하기 위해 dist 디렉터리에 js 파일을 만들 때 사용

### 모듈 이해하기

- export : 기능을 제공
- import : 기능을 이용

```
import {} from ''
import * as sth from ''
```

export default
   - 한 모듈이 내보내는 기능 중 오직 한 개에만 붙일 수 있다.
   - import 문으로 불러올 때 중괄호 없이 사용할 수 있다.

### tsconfig.json

- `compilerOptions` 옵션
- `include` 컴파일 대상 파일 목록

- `module`
   - amd : 웹 브라우저에서 동작
   - commonjs : node.js에서 동작
- `moduleResolution`
   - amd : classic 으로 설정
   - commonjs : node 로 설정
- `target` 트랜스파일할 대상 자바스크립트의 버전
- `paths` import 문에서 from 부분을 해석할 때 찾아야하는 디렉터리
- `sourceMap` true이면 트랜스파일 디렉터리에는 .js.map 파일 생성
   - map 파일은 ts 코드의 어디 위치에 해당하는지 알려줌


## 3장

### 타입 주석

let 변수 이름: 타입 = 초깃값

```
let n: number = 1
```

### 타입 추론

```
let n = 1
```