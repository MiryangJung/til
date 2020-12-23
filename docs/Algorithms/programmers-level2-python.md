---
layout: default
title: Programmers Level 2, Python
parent: Algorithms
---

# [프로그래머스](https://programmers.co.kr/learn/challenges?tab=all_challenges) __Python__ 언어 레벨2 풀이
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## [기능개발](https://programmers.co.kr/learn/courses/30/lessons/42586)

> Min : *0.01ms, 10.2MB*   
> Max : *0.22ms, 10.3MB*

```python
def solution(progresses, speeds):
    answer = []
    
    for i in range(len(speeds)):
        cnt=0
        while progresses[i]<100:
            progresses[i]+=speeds[i]
            cnt+=1
        progresses[i]=cnt
    
    p=progresses[0]
    cnt=0
    for i in range(1,len(speeds)):
        cnt+=1
        if p<progresses[i]:
            answer.append(cnt)
            p=progresses[i]
            cnt=0
        
    answer.append(cnt+1)
    return answer
```

*2020.12.23*



## [다리를 지나는 트럭](https://programmers.co.kr/learn/courses/30/lessons/42583)

> Min : *0.01ms, 10.1MB*   
> Max : *284.26ms, 10.2MB*

```python
def solution(bridge_length, weight, truck_weights):
    q=[0]*bridge_length
    cnt=0
    sum=0
    while q:
        sum-=q.pop(0)
        cnt+=1
        if truck_weights:
            if sum+truck_weights[0]<=weight:
                sum+=truck_weights[0]
                q.append(truck_weights.pop(0))
            else:
                q.append(0)
    return cnt
```

*2020.12.23*



## [프린터](https://programmers.co.kr/learn/courses/30/lessons/42587)

> Min : *0.01ms, 10.2MB*   
> Max : *1.07ms, 10.1MB*

```python
def solution(priorities, location):
    i=0
    l = len(priorities)
    while i != l:
        if priorities[i] < max(priorities[i:]):
            priorities.append(priorities[i])
            priorities.pop(i)
            if location == i:
                location = l-1
            elif location > i:
                location-=1
            i-=1
        i+=1
    return location+1
```

*2020.12.23*



## [멀쩡한 사각형](https://programmers.co.kr/learn/courses/30/lessons/62048)

> Min : *0.01ms, 10.1MB*   
> Max : *4270.77ms, 10.2MB*

```python
def solution(w,h):
    if w==h:return w*h - w
    
    for n in range(w,0,-1):
        if not (w%n or h%n):
            return w*h - ((w/n+h/n)-1)*n
```

> Min : *0.00ms, 10.1MB*   
> Max : *0.01ms, 10.2MB*

```python
from math import gcd

def solution(w,h):
    if w==h:return w*h - w
    g = gcd(w,h)
    return w*h - (w/g+h/g-1)*g
```

*2020.12.23*



## []()

> Min : **   
> Max : **

```python

```

*2020.12.23*



## []()

> Min : **   
> Max : **

```python

```

*2020.12.23*