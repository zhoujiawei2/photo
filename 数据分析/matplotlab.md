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
#如果想让刻度是字符串
a=["1","2","rr","1"]
plt.xticks(range(a.length),a)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MDA5MzY2MjcsLTUwNzY0ODI5OSwxND
M1NzYxMiw2ODAzODAzMTIsMTY3NzA3NTY0MywtMjEzMzU1MjUz
MCw2MjA5ODU0MDAsNTc4MjkwNDksLTE4ODQ5MDE0MTQsNTc4Mj
kwNDldfQ==
-->