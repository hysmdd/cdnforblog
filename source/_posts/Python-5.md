---
title: 政府工作报告词云示例
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Python
date: 2020-06-01 13:14:20
music:
  type: song  
  id: 1351520305
comments: true
---

政府工作报告词云小练习

使用库：

<kbd>jieba库</kbd>

<kbd>wordcloud库</kbd>

<!-- more -->

## 源代码

```python
import jieba
import wordcloud
from imageio import imread
mask = imread("chinamap.png")
f = open("新时代中国特色社会主义.txt","r", encoding="utf-8")
t = f.read()
f.close()
ls = jieba.lcut(t)
txt = " ".join(ls)
w = wordcloud.WordCloud(width=1000,height=700,background_color="white",font_path="msyh.ttc",mask=mask)
w.generate(txt)
w.to_file("wordclouddemo3.png")
```

## 效果演示

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200601131058.png)