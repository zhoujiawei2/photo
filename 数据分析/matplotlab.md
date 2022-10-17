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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQzNTc2MTIsNjgwMzgwMzEyLDE2NzcwNz
U2NDMsLTIxMzM1NTI1MzAsNjIwOTg1NDAwLDU3ODI5MDQ5LC0x
ODg0OTAxNDE0LDU3ODI5MDQ5XX0=
-->