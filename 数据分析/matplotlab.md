> Written with [StackEdit中文版](https://stackedit.cn/).

# matplotlib

axis轴，指的是x轴或者是y轴这种轴

多次plot可以产生多个线，只需要show一次即可
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
my_font=font_manager.FontProperties(fname="字体地址")

#之后在任意需要的地方加上fontproperties=my_font即可
plt.xticks(fontproperties=my_font)
```

添加描述信息
```python
plt.xlabel("")
plt.ylabel("")
plt.title("")
```

网格透明度设置
```python
plt.grid(alpha=0.4)

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQzNzI3NzE1MSwtMjA3MzczOTUwMSwzOT
cxNjU4MzIsLTE1NzA0NzQ3ODEsLTIwMDE1MDIwNjYsLTE3NDY0
ODU0OTQsLTM4MjA4NTg1MSwtNTA3NjQ4Mjk5LDE0MzU3NjEyLD
Y4MDM4MDMxMiwxNjc3MDc1NjQzLC0yMTMzNTUyNTMwLDYyMDk4
NTQwMCw1NzgyOTA0OSwtMTg4NDkwMTQxNCw1NzgyOTA0OV19
-->