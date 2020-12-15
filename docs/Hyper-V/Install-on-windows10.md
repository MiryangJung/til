---
layout: default
title: Install on Windows10
parent: Hyper-V
nav_order: 1
---

## Hyper-V 활성화
1. 관리자 권한으로 `PowerShell` 실행
2. 아래의 명령어 입력

```
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
```

![](https://github.com/MiryangJung/TIL/blob/master/assets/images/Hyper-V/Install/1.PNG?raw=true)

- 컴퓨터를 종료 후 다시시작해야 적용된다.

---
__Refer__ <br>
- [Windows 10에 Hyper-V 설치](https://docs.microsoft.com/ko-kr/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)