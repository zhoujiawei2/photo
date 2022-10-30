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

去掉多余的坐标系，同时使多个坐标系公用坐标轴，主标题，主侧标题，直方图上面多一个折线图
```python
# 改进1: 去掉多余的坐标系
# 面向对象(Object-oriented programming)精确语法
fig, axes = plt.subplots(2, 2, figsize=(6, 6),
                        facecolor="grey",  # 画面背景改为灰色
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


画一个3D图
```python[图片上传中...(image-R6mMyXLO1QKLE7Fx)]
# 改进2: 利用右下角画一个3d图画
# 面向对象OOP精确语法

# 删除右下角坐标系
axes[1, 1].remove()
# 重新添加右下角坐标系（改变为三维坐标系）
ax = fig.add_subplot(2, 2, 4, 
                     projection='3d', facecolor="grey")
ax.stem(seasons, stock1, stock2-stock1)
ax.stem(seasons, stock1, stock2-stock1, 
        linefmt='k--', basefmt='k--', 
        bottom=10, orientation='y')
ax.plot_surface(np.array([1,1,4,4]).reshape(2,2),
                np.array([2.5,10,2.5,10]).reshape(2,2),
                np.array([0]*4).reshape(2,2), 
                alpha=0.2, color='red')
ax.plot_surface(np.array([1,1,4,4]).reshape(2,2),
                np.array([10]*4).reshape(2,2),
                np.array([-2.5,8,-2.5,8]).reshape(2,2),
                alpha=0.2, color='black')
ax.set_xlabel("季度(x)")
ax.set_ylabel("股票1(y)")
ax.set_zlabel("差价(z)")
plt.savefig("images/pic2_6.png", facecolor=fig.get_facecolor())
plt.show()
```
![输入图片说明](/imgs/2022-10-30/FS0JOS5n4nczwnG7.png)

改变北京颜色，该变透明度，该变紧凑度
```python
# 改变坐标系的背景颜色（在画图后改变属性，OOP）
axes[1, 0].set_facecolor('grey')
axes[1, 0].patch.set_alpha(0.2)
axes[0, 0].set_facecolor('red')
axes[0, 0].patch.set_alpha(0.2)
plt.tight_layout()
#tight_layout()是让画面更紧凑
```

## Figure布局控制

gridspec可以用于自定义网格布局


### figure布局控制函数
![输入图片说明](/imgs/2022-10-30/z7dZPNDXQT6bA0dC.png)

### figure相关的参数
![输入图片说明](/imgs/2022-10-30/Yh5XeNdtWX8rzzJK.png)

## 流程

 1. 风格模式很有用

![输入图片说明](/imgs/2022-10-30/CiDnJT5tfKg2GwTL.png)

![输入图片说明](/imgs/2022-10-30/1Oj5TXSQt0IwBmIN.png)

![输入图片说明](/imgs/2022-10-30/02lTidEJ9L8kO11z.png)

 2. 改变全局默认参数
 import matplotlib as mpl
![输入图片说明](/imgs/2022-10-30/DLvktLb8lxQ0hqBT.png)

同时可以打中文和数字公式（多字体）
![输入图片说明](/imgs/2022-10-30/qbqb9gcl85R809sU.png)

3.复用画图代码
![输入图片说明](/imgs/2022-10-30/xClRbxSXjeeep7sw.png)

4。动态图之类的和资源管理
![输入图片说明](/imgs/2022-10-30/26Gn6n4ggL8XAkbq.png)

widget是动态图

## 自学方式

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc3MjIyMzU2NiwzMDU2NDUwOTEsLTEwMD
kwNzE1MTksLTEwNjIxOTAzNTUsNjc2MjQ1MzEyLDE2MDI2OTQx
Miw1Mzg4NzA5MTMsMTYzNjcwNTEyMCwyNDI5MDc3OTgsLTQzMj
U1OTc3OCwyNjE2MDAyLC0xNjYxNDYyODM1LDUyNzM0ODc3LC0y
MDczNzM5NTAxLDM5NzE2NTgzMiwtMTU3MDQ3NDc4MSwtMjAwMT
UwMjA2NiwtMTc0NjQ4NTQ5NCwtMzgyMDg1ODUxLC01MDc2NDgy
OTldfQ==
-->