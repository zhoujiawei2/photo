> Written with [StackEdit中文版](https://stackedit.cn/).

# matplotlib

axis轴，指的是x轴或者是y轴这种轴

```python
	from matplotlib import pyplot as plt
	x=[1,2,5,6]
	y=[3,4,1,7]
	plt.plot(x,y)
	plt.show()
```  
figure图形图标的意思，在这里指画的图 ，figsize图片大小，dpi清晰程度（每英尺像素点数）
```python
	fig=plt.figure(figsize=(20,8),dpi=80)
	
```  
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjY0NDQyNjY1LDY4MDM4MDMxMiwxNjc3MD
c1NjQzLC0yMTMzNTUyNTMwLDYyMDk4NTQwMCw1NzgyOTA0OSwt
MTg4NDkwMTQxNCw1NzgyOTA0OV19
-->