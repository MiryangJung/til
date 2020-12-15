---
layout: default
title: Connect to a remote SQL Server
parent: MSSQL
nav_order: 1
---

# MSSQL 서버 외부 접속 허용

## TCP/IP 허용 및 포트 설정

`SQL Server Configuration Manager` 실행

TCP/IP `Enabled` 로 변경

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/MSSQL/connect-to-a-remote-SQL-Server/1.PNG?raw=true)

TCP PORT를 기본 포트를 제외한 다른 포트로 변경

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/MSSQL/connect-to-a-remote-SQL-Server/5.PNG?raw=true)


## 인증 모드 설정

`MS SQL Server Management Studio` 실행

서버 속성 > 보안 > `SQL Server 및 Windows 인증 모드` 로 설정

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/MSSQL/connect-to-a-remote-SQL-Server/2.PNG?raw=true)


## 방화벽 설정

인바운드 규칙에 MSSQL 포트 허용 규칙 추가

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/MSSQL/connect-to-a-remote-SQL-Server/4.PNG?raw=true)


## 서버 재시작

작업관리자 > 서비스 > `MSSQLSERVER` 재시작

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/MSSQL/connect-to-a-remote-SQL-Server/3.PNG?raw=true)
