---
layout: default
title: String to Slice
parent: GO
nav_order: 3
---


## Go언어 문자열을 슬라이스로 변환하기

CODE 1

```
str := "a,b,c"
fmt.Println(strings.Split(str, ","))
```

OUTPUT 1

```
[a b c]
```

CODE 2

```
str := "abc"
fmt.Println(strings.Split(str, ""))
```

OUTPUT 2

```
[a b c]
```
