---
layout: default
title: 레드햇에 윈도우 폴더 마운트하기
parent: Linux
---


# 레드햇에 윈도우 폴더 마운트하기

## 윈도우 폴더 공유 설정

공유를 위한 폴더 생성

```
D:\>mkdir test
D:\>cd test
```

생성된 폴더 **우클릭** > **속성** > **공유** 에서 공유할 유저를 선택한다.

## 레드햇에서 마운트하기

```
sudo mount -t cifs //192.168.0.1/test /home/miryang/test -o username=miryang,password=123
```

`/etc/fstab` 에 추가

```
//192.168.0.1/test /home/miryang/test cifs username=miryang,password=123 0 0
```