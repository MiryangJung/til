---
layout: default
title: Install on Redhat8
parent: Tibero
nav_order: 1
---

# 레드햇8에 티베로6 설치하기
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Tibero6 다운 및 설치

[tmaxsoft](https://technet.tmaxsoft.com/ko/front/main/main.do) 접속 후 로그인 <br>
다운로드 > 데이터베이스 >  Tibero > Tibero6 > `Linux~.tar.gz` 다운로드

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/Tibero/install-on-redhat8/1.PNG?raw=true)

`호스트 네임` 확인 후 `라이센스` 발급

```
$ hostname
```

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/Tibero/install-on-redhat8/2.PNG?raw=true)


다운받은 파일 압축 해제

```
$ tar xvf tibero6~.tar.gz
```


발급받은 라이센스 `license.xml` 파일을 알맞은 위치에 넣기

```
$ cp license.xml Tibero/tibero6/license/
```


`환경변수` 설정

```
$ export TB_HOME=~/Tibero/tibero6
$ export TB_SID=tibero
$ export LD_LIBRARY_PATH=$TB_HOME/lib:$TB_HOME/client/lib
$ export PATH=$PATH:$TB_HOME/bin:$TB_HOME/client/bin
```


환경 파일 생성

```
$ cd $TB_HOME/config
$ ./gen_tip.sh
```


Tibero 서버를 `NOMOUNT 모드` 로 가동

[Error A](#에러-처리)
{: .label .label-red }

```
$ cd $TB_HOME/bin
$ tbboot nomount
```


tbSQL 유틸리티를 이용해 데이터베이스 접속

[Error B](#에러-처리)
{: .label .label-red }

```
$ tbsql sys/tibero
```


기본적인 `tibero` 데이터베이스 생성

```
SQL> create database "tibero" 
   user sys identified by tibero 
   maxinstances 8 
   maxdatafiles 100 
   character set MSWIN949 
   national character set UTF16 
   logfile 
     group 1 'log001.log' size 100M, 
     group 2 'log002.log' size 100M, 
     group 3 'log003.log' size 100M 
   maxloggroups 255 
   maxlogmembers 8 
   noarchivelog 
     datafile 'system001.dtf' size 100M autoextend on next 100M maxsize unlimited 
     default temporary tablespace TEMP 
       tempfile 'temp001.dtf' size 100M autoextend on next 100M maxsize unlimited 
       extent management local autoallocate 
     undo tablespace UNDO 
       datafile 'undo001.dtf' size 100M autoextend on next 100M maxsize unlimited 
       extent management local autoallocate;
```


`tbboot` 명령어로 티베로를 `NORMAL` 모드로 다시 부팅

```
$ tbboot
```


role, System user 등을 생성하기 위해 `system.sh` 실행

- sys/tibero
- syscat/syscat

```
$ cd $TB_HOME/scripts
$ ./system.sh
```



## 티베로 스튜디오 연결

- Windows 환경에서 설치함
- JRE 1.6 이상 요구

티베로 포트 접속 허용을 위해 방화벽에 포트 추가

```
$ firewall-cmd --permanent --zone=public --add-port=8629/tcp
$ firewall-cmd --reload
$ firewall-cmd --zone=public --list-all
```

[tmaxsoft](https://technet.tmaxsoft.com/ko/front/main/main.do) 접속 후 로그인 <br>
다운로드 > 데이터베이스 >  Tibero > Tibero Studio > `Windows~` 다운로드

`TiberoStudio2~.zip` 압축해제 후 `TiberoStudio.exe` 실행


연결을 위한 정보 입력 후 `TEST` 클릭
- Alias : 별칭으로 자유롭게 입력
- IP : tibero가 구동되고 있는 서버의 IP
- PORT : tibero 포트
- USER / PASSWORD : 아이디 / 패스워드
- SID : 환경변수에 설정한 SID

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/Tibero/install-on-redhat8/3.PNG?raw=true)


연결에 성공하면 `TIBERO STUDIO` 에서 작업 가능

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/Tibero/install-on-redhat8/4.PNG?raw=true)



## 에러 처리

Error A
{: .label .label-red }

```
tbsvr: error while loading shared libraries: libnsl.so.1: cannot open shared object file: No such file or directory
```

Solution A
{: .label .label-green }

```
yum install -y libnsl
```

Error B
{: .label .label-red }

```
tbsql: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
```

Solution B
{: .label .label-green }

```
yum install -y ncurses*
```



---
__Refer__ <br>

- [Hyper-V에 레드햇8 설치](https://miryang.dev/TIL/docs/Hyper-V/install-redhat8/)
- [Tibero6 Online Manual](https://technet.tmaxsoft.com/upload/download/online/tibero/pver-20150504-000001/index.html)