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


## 