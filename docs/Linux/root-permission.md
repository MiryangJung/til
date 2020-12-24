---
layout: default
title:  root 권한 부여
parent: Linux
---


# 레드햇 Redhat 8.0

## sudo 권한 부여

```
# sudo usermod -aG wheel user
# sudo visudo
```

```
## Same thing withou a password
# %wheel ALL=(ALL) NOPASSWD: ALL

>>> 주석 해제
%wheel ALL=(ALL) NOPASSWD: ALL
```

## root 그룹에 포함

```
# vi /etc/passwd

test:x:1001:1001::/home/test

>>> UID, GID 0으로 변경
test:x:0:0::/home/test
```

> 보안상 root 이외의 계정이 uid, gid 0 을 가지는 것은 매우 위험

```
# vi /etc/group
root:x:0:

>>> 유저 추가
root:x:0:test
```
