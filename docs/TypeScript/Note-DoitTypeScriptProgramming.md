---
layout: default
title: ES5
parent: TypeScript
---


## 개발 환경 구성

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

## 