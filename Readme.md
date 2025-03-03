# pydamo简介

> 对大漠插件的简单封装.

- 提供驱动级按键模拟, 以及修改内存、找图找色等功能.
- 需要管理员权限运行pycharm.<br>
- 仅支持32位python, 最好用`python3.6`
- 基于conda的32位python版本管理
  - 使用`conda`安装`win32`环境脚本: `shells\configWin32Env.bat`.
  - 脚本运行完后会输出创建好的python环境路径, 然后参考[pycharm配置conda安装好的python环境](https://blog.csdn.net/weixin_41710606/article/details/86747877?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2.pc_relevant_antiscanv2&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2.pc_relevant_antiscanv2&utm_relevant_index=3)
- 64位解决方案参考末尾其它模拟方式


## 安装

```
shells\configWin32Env.bat       # use conda to create a win32_py36 interpreter

pip install pydamo-test
```


## 使用

- **第一次使用时必须以管理员权限运行pycharm!**

```
from pydamo_0 import Time, DM, Mouse

dm = DM()   # 可指定dm.dll路径DM(path), 若无法使用某些函数dm.f(), 则使用dm.dm.f()来调用.
ms = Mouse(dm)
tt = Time()

print(ms.position)                  # 当前鼠标位置

tt.sleep(1)
x, y = (0, 0)
ms.position = x, y                  # 移动鼠标
ms.click_right(x, y)                # 点击鼠标右键
```

- More examples:
    - [`test.py`](https://github.com/bode135/pydamo/blob/master/test.py)
    - [`知乎笔记`](https://zhuanlan.zhihu.com/p/266519446 "跳转到知乎")


## 使用条件:
1. 32位的python才能运行；
2. 最好使用管理员权限运行（包括pycharm、bat脚本和编译好的exe文件）；
3. 后台绑定挂机为付费的高级功能,我购买的注册码不一定能用很久, 一般用前台键鼠足够。

## 其它模拟方式:
> 这些不支持后台键鼠
1. 64位python可以试试Ctypes和keyboard实现驱动级模拟（前台）
    - [`Ctypes`](https://github.com/bode135/VirtualKey_with_Ctypes "跳转到Ctypes")
    - [`keyboard`](https://github.com/boppreh/keyboard "跳转到keyboard项目的git地址")
2. 如果不是D3D游戏的后台模拟的话，可以试试win API的系统级后台模拟SendMessage；
3. 如果键盘为PS/2圆形接口的话，可用winio模块，但不支持USB键盘。



