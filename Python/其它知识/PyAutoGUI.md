# 1 相关依赖
- 依赖的包
```Python
pyautogui
pyscreeze==0.1.29
opencv-python
```
- 引入模块
```Python
import pyautogui as pgui
import time
```
# 2 常用语句
- 暂停
```Python
time.sleep(2)
'''
暂停2s后继续执行下一行代码
在每个鼠标操作后都应当停顿一下，
防止因为操作频率快于响应速度，
而导致鼠标操作失效
'''

pgui.PAUSE = 1
'''
使每一个pgui的指令施行的间隔都为1s
'''
```
# 3 鼠标操作
- 鼠标位置
```Python
print(pgui.position())
'''
输出当前鼠标坐标位置
'''
```
- 鼠标移动
```Python
pgui.moveTo(100,300,duration=1)
'''
直接把鼠标箭头移动到以屏幕左上角为原点，水平向右为x轴正方向，
竖直向下为y轴正方向，坐标为(100,300)的点上，总用时为1s，
若不填duration，则近乎瞬移鼠标过去
'''

pgui.moveRel(1000,500,duration=1)
'''
从鼠标当前位置开始，向右移动1000px，向下移动500px，用时1s
'''
```
- 鼠标点击
```Python
pgui.doubleClick(1000,1000)
'''在指定坐标位置双击鼠标左键'''
pgui.rightClick(1000,1000)
'''在指定坐标位置双击鼠标右键'''
pgui.middleClick(1000,1000)
'''在指定坐标位置双击鼠标中键'''

pgui.click(10,10)
'''默认单击鼠标左键'''
pgui.click(10,10,button='right')
'''单击鼠标右键'''
pgui.click(10,10,button='middle')
'''单击鼠标中键'''
```
- 鼠标滚动
```Python
pgui.scroll(-200)
'''
向下滚动200单位
滚动完记得time.sleep()几秒
防止操作过快吞掉下一个动作
'''
```
- 鼠标按压
```Python
pgui.mouseDown()
pgui.mouseUp()
'''鼠标按下与释放'''
```
- 鼠标拖拽
```Python
pgui.dragTo(1000,1200,duration=1)
pgui.dragRel(100,500,duration=4)
'''拖动目标到指定位置或向指定方向移动'''
```
# 4 截屏与识图
- 截图
```Python
pgui.screenshot('1.png')
'''截全屏并保存在当下文件夹下为指定名字'''
pgui.screenshot('1.png',region=(0,0,300,400))
'''指定区域，从0,0开始截取X方向为300px，Y方向为400px的一张图'''
```
- 识图
```Python
pyautogui.locateOnScreen('Part.png', region=(0, 0, 600, 800))
'''指定区域找图'''

im = pgui.locateOnScreen('1.png',confidence=0.9)
print(im)
'''
confidence则是精确度，不填默认为1，但这太严格了
这个参数另依赖于opencv-python
若是报错，则重新安装0.1.29版本的pyscreeze，
这样若是没找到对应图像会返回None
'''
```
# 5 键盘操作
- 输入字符串
```Python
pgui.write("bilibili",interval=0.05)
'''
在光标处写入一串字符
注意，一般是要点击一下选中输入框才能执行输入
interval参数是输入每个字符间隔的秒数，可不写
'''
```
- 按键控制
```Python
pgui.press('shift',2,0.05)
'''
表示按下shift键后释放，按2次，每次间隔0.05s
'''

pgui.keyDown()
'''
执行按键，不释放
'''

pgui.keyUp()
'''
执行按键释放
注：无需事先按下
'''

pgui.hotkey('ctrl','c',interval=0.5)
'''
将按键顺序按下，再逆序释放
这里就是执行了一次复制的快捷键操作
'''
```