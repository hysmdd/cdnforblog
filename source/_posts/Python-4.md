---
title: Python实现《三国演义》人物出场次数统计
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Python
date: 2020-05-25 11:11:11
music:
  type: song  
  id: 36990266
comments: true
---

使用Python的第三方库jieba库实现《三国演义》人物出场次数Top20统计。

<!-- more -->

## 代码

```python
import jieba

txt = open("ThreeKingdoms.txt","r", encoding="gb18030").read()
exclude = {"将军","却说","二人","不可","不能","如此","荆州","商议","如何","主公",\
           "军士","左右","军马","引兵","次日","大喜","天下","东吴","于是","今日",\
           "不敢","魏兵","陛下","人马","都督","一人","不知","汉中","众将","只见",\
           "后主","蜀兵","大叫","上马","先主","太守","此人","天子","后人","背后",\
           "城中","何不","一面","忽报","大军","先生","何故","夫人","先锋","然后",\
           "不如","赶来","原来","令人","江东","正是","徐州","忽然","下马","喊声",\
           "成都","因此","未知","百姓","大败","大事","一军","之后","不见","接应",\
           "起兵","引军","军中","可以","进兵","大怒","大惊","心中","以为","不得",\
           "下文","粮草","追赶","分付","一声","分解"
           }
words = jieba.lcut(txt)
counts = {}
for word in words:
    if len(word) == 1:
        continue
    elif word == "诸葛亮" or word == "孔明曰":
        rword = "孔明"
    elif word == "关公" or word == "云长":
        rword = "关羽"
    elif word == "玄德" or word == "玄德曰":
        rword = "刘备"
    elif word == "孟德" or word == "丞相":
        rword = "曹操"
    else:
        rword = word
    counts[rword] = counts.get(rword,0) + 1
for word in exclude:
    del counts[word]
items = list(counts.items())
items.sort(key=lambda x:x[1],reverse=True)
for i in range(20):
    word,count = items[i]
    print("{0:<12}{1:<4}".format(word,count))
```

## 效果图

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200525114839.png)