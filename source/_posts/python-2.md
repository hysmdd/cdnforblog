---
title: 七段数码管绘制系统时间
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Python
date: 2020-05-20 20:13:14
music:
  type: song  
  id: 440353010
comments: true
---

Python代码利用turtle（海龟绘图）实现七段数码管的显示，绘制当前的系统日期。

<!-- more -->

## 代码

```python
#SevennDigitsDrawV1.py
import turtle
import time

def DrawGap():
    turtle.penup()
    turtle.fd(5)
    
def DrawLine(draw):
    DrawGap()
    turtle.pendown() if draw else turtle.penup()
    turtle.fd(40)
    DrawGap()
    turtle.right(90)
    
def DrawDigits(digits):
    DrawLine(True) if digits in [2,3,4,5,6,8,9] else DrawLine(False)
    DrawLine(True) if digits in [0,1,3,4,5,6,7,8,9] else DrawLine(False)
    DrawLine(True) if digits in [0,2,3,5,6,8,9] else DrawLine(False)
    DrawLine(True) if digits in [0,2,6,8] else DrawLine(False)
    turtle.left(90)
    DrawLine(True) if digits in [0,4,5,6,8,9] else DrawLine(False)
    DrawLine(True) if digits in [0,2,3,5,6,7,8,9] else DrawLine(False)
    DrawLine(True) if digits in [0,1,2,3,4,7,8,9] else DrawLine(False)
    turtle.left(180)
    turtle.penup()
    turtle.fd(20)

def DrawDate(date):
    turtle.pencolor("red")
    for i in date:
        if i == "-":
            turtle.write('年',font=("Arial",18,"normal"))
            turtle.pencolor("green")
            turtle.fd(40)
        elif i == "=":
            turtle.write('月',font=("Arial",18,"normal"))
            turtle.pencolor("blue")
            turtle.fd(40)
        elif i == "+":
            turtle.write('日',font=("Arial",18,"normal"))
        else:
            DrawDigits(eval(i))
            
def main():
    turtle.setup(800,300)
    turtle.penup()
    turtle.fd(-300)
    turtle.pensize(5)
    DrawDate(time.strftime("%Y-%m=%d+",time.gmtime()))
    turtle.hideturtle()
    turtle.done()
    
main()
```

## 效果

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200524092806.png)