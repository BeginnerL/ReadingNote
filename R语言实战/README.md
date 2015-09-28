# R语言实战

## 输入
- 向量：x <- c(1,2,3)
- 矩阵：
	- ```xxx <- matrix(1:20, nrow=5, ncol=4)```
	- 按行填充：```xxx <- matrix(1:4, nrow = 2,ncol = 2,byrow=TRUE, demnames=list(C(“R1”,”R2”),C(“C1”,”C2”)))```
	- 按列填充：```xxx <- matrix(1:4, nrow = 2,ncol = 2,byrow=FALSE, demnames=list(C(“R1”,”R2”),C(“C1”,”C2”)))```
- 数组：```z <- array( 1:24,c(2,3,4), dimnames=list(c(“A1”,”A2”), c(“B1”,”B2”,”B3”), c(“C1”,”C2”,”C3”,”C4”)))```
- 数据框：
	- 赋值:
		-  `xx <- data.frame(col1,col2,col3)`
		-  `xx <- data.frame(col1,col2,col3,row.names=col1)`
	- 取值
		- `xx[c(col1,col3)]`
		- `xx$col1`
		- `attach(xx);summary(col1);detach(xx)`
		- `with(xx,{summary(col1)})`
			- with中如果要创建全局变量，使用`<—`，否则`<-`生命周期只在with里面
- 因子：
	- `xx <- factor(xxx)`
	- `xx <- factor(xxx,order=TRUE)`
	- `xx <- factor(xxx,order=TRUE,level=c(x1,x2,x3))`
- 列表:`xx <- list(x1,x2,x3)`
	- `xx[[1]]`
	- `xx[[‘x2’]]`

## 输入数据
- `xx <- read.table(‘xx.csv’, header=True, sep=“,”, row.names=“xx”)`
	- 分隔符默认`””`，表示”\s”

## 统计函数
* mean
* sd：标准差
* cor：相关系数

## 管理函数
|函数|功能|
|:——:|:——:|
|getwd()|显示当前的工作目录|
|setwd(“mydirectory”)|修改当前的工作目录为mydirectory|
|ls()|列出当前工作空间中的对象|
|rm(objectlist)|移除(删除)一个或多个对象|
|help(options)|显示可用选项的说明|
|options()|显示或设置当前选项|
|history(#)|显示最近使用过的#个命令(默认值为25)|
|savehistory(“myfile”)| 保存命令历史到文件myfile中(默认值为.Rhistory) | 
|loadhistory(“myfile”)|载入一个命令历史文件(默认值为.Rhistory)|
|save.image(“myfile”)| 保存工作空间到文件myfile中(默认值为.RData)|
|save(objectlist, file=“myfile”)| 保存指定对象到一个文件中|
|load(“myfile”)|读取一个工作空间到当前会话中(默认值为.RData)|
|q()|退出R。将会询问你是否保存工作空间|

- 显示位数：`options(digits=3)`
- 查看数据基本统计参数:`summary(x)`
- 设定输出:
	- 文本输出
		- `sink(filename,append=TRUE,split=TRUE)`,后两个参数可选
		- `sink()`
	- 图形输出：
		- `pdf(“xxx.pdf”)`
		- `png()`
		- `jpeg()`
		- `bmp()`
		- `tiff()`
		- …
		- `dev.off()`：退出图形输出，不用这句的话图形文件看不了

## 对象函数
- `length`：成分数量
- `dim`：维度，向量无效
- `str`：结构
- `class`：类型（numeric,character...）
- `mode`：对象模式
- `names`：显示各成分名称
- `cbind`：按列合并
- `rbind`：按行合并
- `head`：前面部分（6行）
- `tail`：尾部（6行）
- `ls`：当前对象列表
- `rm`：删除对象
- `xxx<-edit()`：编辑并另存
- `fix`：直接编辑对象

## 画图
- 新窗口绘制：`dev.new()`
- 更改绘制的图像：`dev.next()`,`dev.prev()`
- `plot`：
	- type=‘b’：同时绘制点和线
	- `pch`：点的符号
	![Alt text](./1443270606196.png)
	- `cex`:指定点的大小
	- `lty`：线类型
	![Alt text](./1443270770523.png)
	- `lwd`：线宽
	- 颜色：
		- `col`：颜色
		- `bg`：背景
		- `col.axis`：坐标轴刻度颜色
		- `col.lab`:坐标轴标签颜色
		- `col.main`：标题颜色
		- `col.sub`：副标题颜色
		- `fg`：前景色
		- 表示方法：
			- `col=1`
			- `col=“white”`
			- `col=“#FFFFFF”`
			- `col=rgb(1,1,1)`
			- `col=hsv(0,0,1)`
		- 连续颜色：
			- `rainbow()`
			- `heat.colors()`
			- `terrain.colors()`
			- `topo.colors()`
			- `cm.colors()`
	- 文本：
		- `cex.aixs`：坐标轴刻度文字缩放
		- `cex.lab`：坐标轴标签缩放
		- `cex.main`：标题缩放
		- `cex.sub`：副标题缩放
		- 添加文本
			- `mtext(‘xx’, side=xx, line=xx, cex.lab=x, ...)`：边界添加文本
			- `text(‘xx’, side=xx, line=xx, cex.lab=x, ...)`：绘图区添加文本
			- 传入位置，文本均为向量可以批量添加
		- 数学标注：参考`demo(plotmath)`
		- 字体：
			- `font`:1=常规，2=粗体，3=斜体，4=粗斜体，5=符号字体adobe符号编码
			- `font.axis`
			- `font.lab`
			- `font.main`
			- `font.sub`
			- `ps`：字体磅值，最终文本大小=ps×cex
			- `family`:字体族，`serif`衬线,`sans`无衬线,`mono`等宽
	- 尺寸：
		- `pin`：图形尺寸，二维
		- `mai`：边界大小（英寸），四维，下，左，上，右
		- `mar`：边界大小（英分），四维，下，左，上，右
	- 坐标轴：
		- `xlim`
		- `ylim`
		- `xlab`
		- `ylab`
		- `ann=FALSE`:移除par的默认标题，标签
		- `title(main=“xx”, sub=“xx”, xlab=“xx”, ylab=“xx”, col.main=“x”…)`
		- `axis`：自定义坐标轴
			- `side`:1，2，3，4分别是下左上右
			- `at`：绘制tick刻度线位置，数字型向量
			- `labels`：字符型向量，刻度的文字标签
			- `pos`：坐标轴相交位置的值
			- `lty`：线类型
			- `col`
			- `las`：标签是否与坐标轴平行（=0)，垂直（=2）
			- `tck`：刻度线长度
				- 默认-0.01
				- 负值表示图形外侧
				- 正值表示图形内侧
				- 0表示禁用刻度
				- 1绘制网格线
			- `axes=FALSE`:禁用全部坐标轴
			- `xaxt=“n”`：禁用x轴
			- `yaxt=“n”`：禁用y轴
	- 参考线：
		- `abline(h=c(..))`
		- `abline(v=c(..))`
	- 图例：`legend()`
		- `location`
			- 直接给出x,y坐标
			- `locator(1)`,然后鼠标点击
			- `bottom`,`bottomleft`等，可以使用`inset=`指定向图形内侧移动大小
		- `title`：图例标题
		- `legend`:字符型向量
		- `bty`：盒子样式
		- `bg`
		- `cex`
		- `text.col`
		- `horiz=TRUE`：水平放置
- 子图：
	- `par(mfrow=c(2,2))`
	- `layout(matrix(c(1,1,2,3),2,2,byrow=TRUE))`:第一行一副，第二行两幅
	- `layout(matrix(c(1,1,2,3), 2, 2, byrow=TRUE), widths=c(3,1), heights=c(1,2))`:第一行一副，第二行两幅，两行等高，但是不等宽
	- `par(fig=c(x1,x2,y1,y2))`：在同一幅图中精细布局，第二幅开始后面要加上`new=TRUE`
		> ![Alt text](./1443273850468.png)
