> Written with [StackEdit中文版](https://stackedit.cn/).

# matplotlib

## 基础共通知识

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

网格以及透明度设置
```python
plt.grid(alpha=0.4)

```
在原图基础上进行调整显示
```python
#显示一个范围
plt.xlim(2.5,4.5)
plt.ylim(1.5,6.5)
```
plt.ylim()

对于一条线进行标注(图例)
```python
plt.plot(x,y,label="313")
plt.legend()
#legend很特殊，在这里设置字体用prop=
#其他都是fontproperties
#legend()loc参数调整位置，prop调整字体
```

线颜色、风格、粗细、透明度的改变
```python
plt.plot(x,y,color="orange",linestyle='--',linewidth=5,alpha=0.5)

```

![输入图片说明](/imgs/2022-10-30/cmmTGSFURlwCn52g.png)

绘制散点图
```python
plt.scatter(x,y)
```

## 画多个图

画两个图
```python
plt.subplot(211)
plt.bar()
#bar是直方图
plt.subplot(212)
plt.plot()
plt.show()
#subplot()就是一个标记图分割的函数，211，分别表示2行1列第一个图
```
使用面向对象画多个图
```python
fig,axes=plt.subplots(2,1,figsize=(6,6))
axes[0].bar()
axes[1].plot()
plt.show()
#subplot()就是一个标记图分割的函数，211，分别表示2行1列第一个图
```
改进
```python
# 面向对象(Object-oriented programming)精确语法
# fig: 画面; axes: 2行2列坐标系（储存在numpy数组中）
fig, axes = plt.subplots(2, 2, figsize=(6, 6))
axes[0, 0].bar(seasons, stock1)  # 左上角(0行0列)坐标系
axes[0, 1].plot(seasons, stock2, "b^--")  # 右上角(0行1列)坐标系
ax = axes[1, 0]  # 左下角(1行0列)坐标系
# 左下角画散点图(scatterplots)
ax.scatter(seasons, # 季度（横坐标）
           stock2-stock1,  # 股票差价（纵坐标）
           s=[10, 20, 50, 100], # size字符大小
           c=['r', 'b', 'c', 'y']) # color颜色

axes[0, 0].set_title("股票1")  # 左上角(0行0列)标题
axes[0, 1].set_title("股票2")  # 右上角(0行1列)标题
ax.set_ylabel("差价(股票1-股票2)")  # 左下角(1行0列)y轴标注
# plt.savefig("images/pic2_4.png")
plt.show(
```


![输入图片说明](/imgs/2022-10-30/tMeFwqUkTGx9wJ6W.png)

```python
# 改进1: 去掉多余的坐标系
# 面向对象(Object-oriented programming)精确语法
fig, axes = plt.subplots(2, 2, figsize=(6, 6),
                        facecolor="gre![输入图片说明](/imgs/2022-10-30/imyv9izffZkupcgq.png)y",  # 画面背景改为灰色
                        sharex=True, sharey=True)  # 共享xy轴坐标系
axes[0, 0].bar(seasons, stock1)
axes[0, 1].plot(seasons, stock2, "b^--")
ax = axes[1, 0]
ax.plot(seasons, stock2-stock1, "--", color="black")
ax.scatter(seasons, stock2-stock1, 
           s=[10, 20, 50, 100],
           c=['r', 'b', 'c', 'y'])
ax.set_ylabel("差价(股票1-股票2)")
axes[0, 0].set_title("股票1")
axes[0, 1].set_title("股票2")

# 可以删除最后一个坐标系
axes[1, 1].remove()
axes[0, 0].plot(seasons, stock1, 'r+-')
fig.suptitle("股票分析图")
fig.supylabel("股价")
fig.supxlabel("季度")
# plt.savefig("images/pic2_5.png", facecolor=fig.get_facecolor()) # 注: 保存图片底色要重新设置
```
![输入图片说明](/imgs/2022-10-30/5YQUvrVC48SDJd8o.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNTM0NzEzNzMsMTYwMjY5NDEyLDUzOD
g3MDkxMywxNjM2NzA1MTIwLDI0MjkwNzc5OCwtNDMyNTU5Nzc4
LDI2MTYwMDIsLTE2NjE0NjI4MzUsNTI3MzQ4NzcsLTIwNzM3Mz
k1MDEsMzk3MTY1ODMyLC0xNTcwNDc0NzgxLC0yMDAxNTAyMDY2
LC0xNzQ2NDg1NDk0LC0zODIwODU4NTEsLTUwNzY0ODI5OSwxND
M1NzYxMiw2ODAzODAzMTIsMTY3NzA3NTY0MywtMjEzMzU1MjUz
MF19
-->