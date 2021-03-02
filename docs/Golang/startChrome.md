---
layout: default
title: start Chrome with golang
parent: GO
---


## Run chrome with golang

```
	err := exec.Command("cmd", "/C", "start", "chrome.exe", "https://google.com").Run()
	if err != nil {
		log.Println(err)
	} 
```