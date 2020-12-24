---
layout: default
title: SSH 구동
parent: Linux
---


# 레드햇 Redhat 8.0

## ssh 포트 변경

`sshd_config` 파일을 연다.

```
# vi /etc/ssh/sshd_config
```

`# Port 22` 부분의 주석을 해제하고, 포트를 수정한다.

```
Port 12345
```

## ssh 서비스 시작

```
# systemctl start sshd.service
```

## 방화벽 오픈

```
# firewall-cmd --zone=public --add-port=12345/tcp --permanent
# firewall-cmd --reload
# systemctl restart firewalld.service
```

