---
title: 解决pip异常:No module named 'pip'
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Python
date: 2020-05-19 21:10:00
music:
	type: song
	id: 165364
comments: true
---



学习Python过程中，pip安装模块的时候提示我有新版本更新，更新之后不知道为什么就无法使用pip命令了，一直提示<kbd>ModuleNotFoundError: No module named 'pip'</kbd>。

<!-- more -->

```
Traceback (most recent call last):
  File "e:\python\lib\runpy.py", line 193, in _run_module_as_main
    return _run_code(code, main_globals, None,
  File "e:\python\lib\runpy.py", line 86, in _run_code
    exec(code, run_globals)
  File "E:\python\Scripts\pip.exe\__main__.py", line 5, in <module>
ModuleNotFoundError: No module named 'pip'
```

## 解决方案

```
Python -m ensurepip
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519210256.png)

```
python -m pip install --upgrade pip
```

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20200519210329.png)

{% note success, 至此，pip命令修复完成，又可以正常使用了 %}