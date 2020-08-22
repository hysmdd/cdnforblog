---
title: 七段数码管带时间倒计时效果
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Python
date: 2020-05-24 11:11:11
music:
  type: song  
  id: 509728841
comments: true
---

带刷新时间的时间倒计时效果，使用随机数生成随机色，实现不同数字间的颜色变化。

<!-- more -->

```python
import turtle
import time
import random

def drawLine(draw):
    turtle.pendown() if draw else turtle.penup()
    turtle.fd(70)
    turtle.right(90)

def drawDigit(digit,color):
    turtle.pencolor(color)
    drawLine(True) if digit in [2, 3, 4, 5, 6, 8, 9] else drawLine(False)
    drawLine(True) if digit in [0, 1, 3, 4, 5, 6, 7, 8, 9] else drawLine(False)
    drawLine(True) if digit in [0, 2, 3, 5, 6, 8, 9] else drawLine(False)
    drawLine(True) if digit in [0, 2, 6, 8] else drawLine(False)
    turtle.left(90)
    drawLine(True) if digit in [0, 4, 5, 6, 8, 9] else drawLine(False)
    drawLine(True) if digit in [0, 2, 3, 5, 6, 7, 8, 9] else drawLine(False)
    drawLine(True) if digit in [0, 1, 2, 3, 4, 7, 8, 9] else drawLine(False)
    turtle.penup()
    turtle.left(180)
    turtle.fd(-70)
    time.sleep(0.8)
    turtle.clear()

def randomColor():
    num1 = random.random()
    num2 = random.random()
    num3 = random.random()
    return num1,num2,num3

def main():
    turtle.setup(500,500)
    turtle.penup()
    turtle.fd(-25)
    turtle.pensize(5)
    turtle.speed(0.1)
    for i in range(1,11):
        drawDigit(10-i,randomColor())
        # randomColor()
    turtle.write("浩浩❤元元",font=("Arial",55,"normal"),align="center")
    turtle.hideturtle()
    turtle.done()

main()
```

