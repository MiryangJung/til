---
layout: default
title: Convert raw to png
parent: GO
---


## Golang Convert raw []byte to png image

흑백 16비트 raw 데이터를 png로 변환해서 저장하기

```
img := image.NewGray16(image.Rect(0, 0, width, height))
img.Pix = imageByte

f, _ := os.Create("test.png")
defer f.Close()

png.Encode(f, img)
```