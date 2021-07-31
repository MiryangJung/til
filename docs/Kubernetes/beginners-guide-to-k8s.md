---
layout: default
title: 강의노트. 쿠버네티스 안내서
parent: Kubernetes
---


# 강의노트. 쿠버네티스 안내서
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

> [쿠버네티스 안내서](https://subicura.com/k8s/)

## 개발 환경 준비

### minikube 설치

1. `minikube` 다운 및 설치
   - 쿠버네티스는 최소 3대의 마스터 서버와 n개의 노드 서버가 필요
   - 개발 테스트를 위해 구축하기엔 무리가 있음
   - 로컬 쿠버네티스를 빠르게 설정해주는 도구
2. **Hyper-V** 활성화  
    ```
    DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
    bcdedit /set hypervisorlaunchtype auto
    ```
3. `minikube` 기본 명령어
   ```
    # minikube 상태확인
    minikube status

    # minikube 실행 (윈도우는 관리자모드에서)
    minikube start

    # 특정 k8s 버전 실행
    minikube start --kubernetes-version=v1.20.0

    # 특정 driver 실행
    minikube start --driver=virtualbox --kubernetes-version=v1.20.0

    # minikube ip 확인 (접속테스트시 필요)
    minikube ip

    # minikube 종료
    minikube stop

    # minikube 제거
    minikube delete
   ```

### kubectl 설치

쿠버네티스 CLI 도구

1. `kubectl` 설치 (윈도우)
    ```
    C:\kube> curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.20.0/bin/windows/amd64/kubectl.exe
    ```
2. 환경 변수에 **C:\kube** 추가
3. `kubectl` 버전 확인
   ```
   kubectl version
   ```

## 워드프레스 배포해보기

1. [yml 파일](https://subicura.com/k8s/code/guide/index/wordpress-k8s.yml) 다운로드
2. 배포 명령어 실행
   ```
   kubectl apply -f wordpress.yml
   ```
3. 배포 상태 확인 및 포트 확인
   ```
   kubectl get all
   ```
4. minikube ip 확인
   ```
   minikube ip
   ```
5. **ip:port** 로 접속
6. 워드프레스 리소스 제거
   ```
   kubectl delete -f wordpress.yml
   ```

## kubectl 명령어

### apply - 상태 설정하기

원하는 리소스의 상태를 YAML로 작성 후 `apply` 명령어로 선언

```
kubectl apply -f [file or url]
```

### get - 리소스 목록 보기

pod 조회  
```
> kubectl get pod

NAME                              READY   STATUS    RESTARTS   AGE
wordpress-5f59577d4d-mg7xw        1/1     Running   0          20m
wordpress-mysql-545d9c6dc-crzxl   1/1     Running   0          20m
```

Pod, ReplicaSet, Deployment, Service, Job 조회 => all  
```
> kubectl get all

NAME                                  READY   STATUS    RESTARTS   AGE
pod/wordpress-5f59577d4d-mg7xw        1/1     Running   0          23m
pod/wordpress-mysql-545d9c6dc-crzxl   1/1     Running   0          23m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP        55m
service/wordpress         NodePort    10.98.118.73   <none>        80:30021/TCP   23m
service/wordpress-mysql   ClusterIP   10.109.69.8    <none>        3306/TCP       23m

NAME                              READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/wordpress         1/1     1            1           23m
deployment.apps/wordpress-mysql   1/1     1            1           23m

NAME                                        DESIRED   CURRENT   READY   AGE
replicaset.apps/wordpress-5f59577d4d        1         1         1       23m
replicaset.apps/wordpress-mysql-545d9c6dc   1         1         1       23m
```

결과 포맷 변경
```
kubectl get pod -o wide
kubectl get pod -o yaml
kubectl get pod -o json
```

### describe - 리소스 상세 상태보기

```
> kubectl describe [TYPE] [NAME] or [TYPE]/[NAME]

Name:         wordpress-5f59577d4d-mg7xw
Namespace:    default
Priority:     0
Node:         minikube/1.2.3.4
Start Time:   Sun, 01 Aug 2021 00:45:06 +0900
Labels:       app=wordpress
              pod-template-hash=5f59577d4d
              tier=frontend
Annotations:  <none>
Status:       Running
IP:           1.2.3.4
IPs:
  IP:           1.2.3.4
...
```

### delete - 리소스 제거

```
kubectl delete [TYPE] [NAME] or [TYPE]/[NAME]
```

### logs - 컨테이너 로그 조회

- `-f` : 실시간 로그
- `-c` : 하나의 pod에 여러 개의 컨테이너가 있는 경우 컨테이너 지정

```
kubectl logs [POD NAME]

# 실시간 로그
kubectl logs -f [POD NAME]
```

### exec - 컨테이너 명령어 전달

- `-it` : 쉘로 접속
- `-c` : 여러 개의 컨테이너가 있는 경우 컨테이너 지정

```
kubectl exec [-it] [POD_NAME] -- [COMMAND]

> kubectl exec -it wordpress-5f59577d4d-lmtp8 -- bash
root@wordpress-5f59577d4d-lmtp8:/var/www/html# ls
index.php        wp-admin              wp-config.php  wp-links-opml.php  wp-settings.php
license.txt      wp-blog-header.php    wp-content     wp-load.php        wp-signup.php
readme.html      wp-comments-post.php  wp-cron.php    wp-login.php       wp-trackback.php
wp-activate.php  wp-config-sample.php  wp-includes    wp-mail.php        xmlrpc.php
```

### config - 설정 관리

```
# 현재 컨텍스트 확인
kubectl config current-context

# 컨텍스트 설정
kubectl config use-context minikube
```

## Pod

쿠버네티스에서 관리하는 가장 작은 배포 단위  
`Pod` 는 여러 개의 컨테이너를 포함

