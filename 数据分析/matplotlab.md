> Written with [StackEdit中文版](https://stackedit.cn/).

# matplotlib

axis轴，指的是x轴或者是y轴这种轴

```python
	from matplotlib import pyplot as plt
	x=[1,2,5,6]
	y=[3,4,1,7]
	plt.plot(x,y)
	plt.show()
	#show就会清楚plt中的内容
```  
figure图形图标的意思，在这里指画的图 ，figsize图片大小，dpi清晰程度（每英尺像素点数）
```python
	fig=plt.figure(figsize=(20,8),dpi=80)
	
```  
图片保存
```python
	plt.savefig("./t1.png")
	#.svg是矢量图格式，放大不会有锯齿
	
```  
设置刻度
```python
x=range(50)
plt.xticks(x)#x轴
plt.yticks(x)#x轴
```
```python
#如果想让刻度是字符串
a=["1","2","rr","1"]
plt.xticks(range(a.length),a)
```
```python
#如果想让刻度文字方向旋转
x=range(50)
plt.xticks(x,rotation=90)
```

打出中文
```python    
plt.xticks(fontproperties="STSong")

```


用这个:可以修改默认字体
import matplotlib matplotlib.rc("font",family='FangSong')

可以引入一个设置一个字体变量
```python
import matplotlib.font_manager
my_front=font_manager.FontProperties(fname="d")
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzU4ODQ5MTk2LC0yMDAxNTAyMDY2LC0xNz
Q2NDg1NDk0LC0zODIwODU4NTEsLTUwNzY0ODI5OSwxNDM1NzYx
Miw2ODAzODAzMTIsMTY3NzA3NTY0MywtMjEzMzU1MjUzMCw2Mj
A5ODU0MDAsNTc4MjkwNDksLTE4ODQ5MDE0MTQsNTc4MjkwNDld
fQ==
-->