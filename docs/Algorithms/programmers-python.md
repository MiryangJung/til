---
layout: default
title: Programmers, Python
parent: Algorithms
nav_order: 4
---

# [프로그래머스](https://programmers.co.kr/learn/challenges?tab=all_challenges) __Python__ 언어 풀이
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## [모의고사](https://programmers.co.kr/learn/courses/30/lessons/42840)

> Min : *0.01ms, 10.2MB* <br>
> Max : *3.05ms, 10.3MB*

```python
def solution(answers):
    
    arr1, arr2, arr3 = [1,2,3,4,5], [2,1,2,3,2,4,2,5], [3,3,1,1,2,2,4,4,5,5]
    cnt1, cnt2, cnt3 = 0,0,0
    
    for i in range(len(answers)):
        ans = answers[i]
        cnt1+=ans==arr1[i%5]
        cnt2+=ans==arr2[i%8]
        cnt3+=ans==arr3[i%10]
    
    m = max(cnt1,cnt2,cnt3)
    
    answer = []
    if m == cnt1:
        answer.append(1)
    if m == cnt2:
        answer.append(2)
    if m == cnt3:
        answer.append(3)
    
    return answer
```

*2020.12.16*


## [K번째수](https://programmers.co.kr/learn/courses/30/lessons/42748)

> Min : *0.01ms, 10MB* <br>
> Max : *0.01ms, 10.3MB*

```python
def solution(array, commands):
    answer = []
    for c in commands:
        answer.append((sorted(array[c[0]-1:c[1]]))[c[2]-1])
    return answer
```

*2020.12.16*


## [체육복](https://programmers.co.kr/learn/courses/30/lessons/42862)

> Min : *0.01ms, 10.1MB* <br>
> Max : *0.01ms, 10.3MB*

```python
def solution(n, lost, reserve):  
    arr = [1]*(n+1)
    
    for n in lost:
        arr[n]=0
    for n in reserve:
        arr[n]+=1
    for i in range(1,len(arr)-1):
        if arr[i]==0 and arr[i-1]==2:
            arr[i]=1
            arr[i-1]=1
        elif arr[i]==0 and arr[i+1]==2:
            arr[i]=1
            arr[i+1]=1
            
    answer = arr.count(1) + arr.count(2) -1
    
    return answer
```

*2020.12.16*



## [2016년](https://programmers.co.kr/learn/courses/30/lessons/12901)

> Min : *0.00ms, 10MB* <br>
> Max : *0.01ms, 10.3MB*

```python
def solution(a, b):
    
    day = ["THU","FRI","SAT","SUN","MON","TUE","WED"]
    month = [31,29,31,30,31,30,31,31,30,31,30,31]
    
    s = 0
    
    for i in range(0,a-1):
        s += month[i]
    
    return day[(s+b)%7]
```

*2020.12.16*


## [가운데 글자 가져오기](https://programmers.co.kr/learn/courses/30/lessons/12903)

> Min : *0.00ms, 10MB* <br>
> Max : *0.00ms, 10.2MB*

```python
def solution(s):
    answer = s[len(s)//2-1+len(s)%2:len(s)//2+1]
    return answer
```

*2020.12.16*

## [나누어 떨어지는 숫자 배열](https://programmers.co.kr/learn/courses/30/lessons/12910)

> Min : *0.01ms, 10MB* <br>
> Max : *2.88ms, 13.4MB*

```python
def solution(arr, divisor):
    answer = []
    
    for n in arr:
        if not n%divisor:
            answer.append(n)
    
    return sorted(answer) if answer else [-1]
```

*2020.12.17*

## [두 정수 사이의 합](https://programmers.co.kr/learn/courses/30/lessons/12912)

> Min : *0.00ms, 10.1MB*   
> Max : *319.92ms, 10.2MB*

```python
def solution(a, b):
    return sum(range(min(a,b),max(a,b)+1))
```

*2020.12.18*

## [문자열 내 마음대로 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/12915)

> Min : *0.00ms, 10.2MB*   
> Max : *0.02ms, 10.2MB*

```python
def solution(strings, n):
    return sorted(sorted(strings), key=lambda s:s[n])
```

*2020.12.18*

## [문자열 내림차순으로 배치하기](https://programmers.co.kr/learn/courses/30/lessons/12917)

> Min : *0.01ms, 10.2MB*   
> Max : *0.07ms, 10.1MB*

```python
def solution(s):
    return ''.join(sorted(s,reverse=True))
```

*2020.12.18*

## [문자열 다루기 기본](https://programmers.co.kr/learn/courses/30/lessons/12918)

> Min : *0.00ms, 10.1MB*   
> Max : *0.01ms, 10.4MB*

```python
def solution(s):
    return s.isdecimal() and len(s)==4 or len(s)==6
```

*2020.12.18*

## [서울에서 김서방 찾기](https://programmers.co.kr/learn/courses/30/lessons/12919)

> Min : *0.00ms, 10.1MB*   
> Max : *0.01ms, 10.2MB*

```python
def solution(seoul):
    return "김서방은 " + str(seoul.index("Kim")) + "에 있다"
```

*2020.12.18*

## [수박수박수박수박수박수?](https://programmers.co.kr/learn/courses/30/lessons/12922)

> Min : *0.00ms, 10.1MB*   
> Max : *0.00ms, 10.2MB*

```python
def solution(n):
    return "수박"*(n//2)+"수박"[:n%2]
```

*2020.12.18*

## [문자열을 정수로 바꾸기](https://programmers.co.kr/learn/courses/30/lessons/12925)

> Min : *0.01ms, 10.3MB*   
> Max : *0.02ms, 10.4MB*

```python
def solution(s):
    return int(s)
```

*2020.12.18*

## [내적](https://programmers.co.kr/learn/courses/30/lessons/70128

> Min : *0.01ms, 10.2MB*   
> Max : *0.18ms, 10.2MB*

```python
def solution(a, b):
    answer = 0
    for i in range(len(a)):
        answer += a[i]*b[i]
    return answer
```

*2020.12.18*
