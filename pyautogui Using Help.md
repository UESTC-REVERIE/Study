[TOC]

## Pyautogui-python自动化库的使用

-----

### 基础知识

- 屏幕坐标以右上角为原点，右下角为边界（1919，1079）

### API

#### 鼠标控制

1. pyautogui.position() 返回当前鼠标的位置坐标信息作为一个参数接受时返回类型为<calss Point>，当用两个参数接受时返回两个<int>

2. ```pyautogui.moveTo(posX,posY,duration)``` 世界坐标的移动，将鼠标在duration(一定期间内)移动到（posX,posY）位置，一般情况下为匀速运动，也可以通过一下方法实现变速运动：(PyAutoGUI有30种缓动/渐变函数，可以通过pyautogui.ease*?查看)

   ```python
   pyautogui.moveTo(100, 100, 2, pyautogui.easeInQuad) # 开始很慢，不断加速
   pyautogui.moveTo(100, 100, 2, pyautogui.easeOutQuad) # 开始很快，不断减速
   pyautogui.moveTo(100, 100, 2, pyautogui.easeInOutQuad) # 开始和结束都快，中间比较慢
   pyautogui.moveTo(100, 100, 2, pyautogui.easeInBounce) # 一步一徘徊前进
   pyautogui.moveTo(100, 100, 2, pyautogui.easeInElastic) # 徘徊幅度更大，甚至超过起点和终点
   ```

   

3. ```pyautogui.moveRel(posX,posY,duration) ```相对位置的移动，以鼠标所在位置为新的原点建立坐标系进行移动（右下为第一象限）

4. ```pyautogui.click(posX,posY,button,duration,clicks,interval)``` 鼠标点击事件（包括鼠标在duration内移动到相应位置，键的类型（'right', 'left', 'middle'）,连续点击定义（clicks=times,interval=sleepTime））

5. ```pyautogui.scoll(<int>, posX, posY)``` 控制鼠标滚轮，向上为正数（手动感受为100倍缩放）

6. ```pyautogui.mouseDown(posX,posY,button)``` and ```pyautogui.mouseUp(posX,posY,button)``` 分开处理鼠标的按下和松开

7. ```pyautogui.dragTo(posX,posY,button,duration)``` and``` pyautogui.dragRel(posX,posY,button,duration)``` 按下鼠标并进行拖拽


#### 模拟按键

1. ```pyautogui.typewrite(<string>,interval)```  以interval为输入间隔，控制键盘打出字符，只能用于单个字符键，也可以是```pyautogui.typewrite(['a', 'b', 'c'], interval=0.1)```列表形式

2. ```pyautogui.press(<pyautogui.KEYBOARD_KEYS>)``` 模拟按一下按键（可以像typewrite一样传输列表），对应的有按下按键不放```pyautogui.keyDown()```，释放按键```pyautogui.keyUp()```

3. ```pyautogui.hotkey('key1','key2','key3'......)``` 用于组合按键


#### 图像处理

1. 一系列使用Thinker实现，封装的消息弹窗函数：
   ```pyautogui.alert(text='', title='', button='OK') #显示一个简单的带文字和OK按钮的消息弹窗。用户点击后返回button的文字。```

   ```pyautogui.confirm(text='', title='', buttons=['OK', 'Cancel']) # 显示OK和Cancel按钮的消息弹窗。用户点击后返回button的文字。``` 
   ```pyautogui.confirm(text='', title='', buttons=range(10)) # 显示0-9十个按键的消息弹窗。用户点击后返回button的文字。```
   ```pyautogui.prompt(text='', title='' , default='') # 可以输入的消息弹窗，带OK和Cancel按钮。用户点击OK按钮返回输入的文字，点击Cancel按钮返回None。```
   ```pyautogui.password(text='', title='', default='', mask='*') # 样式同prompt()，用于输入密码，消息用*表示。带OK和Cancel按钮。用户点击OK按钮返回输入的文字，点击Cancel按钮返回None。```

2. 截屏函数：
   ```pyautogui.screenshot(posX,posY,width,height,<文件名>)``` 

3. 用图片定位屏幕中某图像位置：
   ```pyautogui.locateOnScreen('图片名称（或路径）')```
    ```pyautogui.center(posX,posY,width,height)``` 可以用于返回图片中心点

