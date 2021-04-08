---
layout: default
title: 인프런 팀 개발을 위한 Git, GitHub 입문 강의 노트
parent: Git
---

> [팀 개발을 위한 Git, GitHub 입문](https://inf.run/pr3d) 강의 노트

## Github 에 코드를 올리는 과정

1. Git 초기화 `git init`
    - .git 이라는 폴더가 생성됨
    - 로컬 저장소라고 부름
    - 한 폴더에 하나의 로컬 저장소
2. 원하는 파일만 선택하여 커밋하기
    - `git add README.md`
    - `git commit -m "설명"`
3. 생성한 커밋 보기
    - `git log`
4. 로컬 저장소에 github 저장소 연결
    - `git remote add origin https://github.com/~`
5. 만든 커밋 푸시하기
    - `git push origin master`

### Git 전역 사용자 설정
- `git config --global user.name "MiryangJung"`
- `git config --global user.email miryang.dev@gmail.com`

### 커밋
1. 의미 있는 변동사항을 묶어서 만든다.
2. 버튼 클릭 버그를 고치는데 5가지 파일을 수정했다면 5가지를 묶어 하나의 커밋으로
3. 동료 개발자 또는 미래의 내가 버튼 클릭 버그를 고치는데 어떤 파일을 수정했는지 쉽게 파악 가능
    

