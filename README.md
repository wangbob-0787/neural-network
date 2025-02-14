# neural-network
用 Python 编写的一个简单的神经网络
### 1 简单的线性预测器和分类器
#### 1.1 千米转化为英里的预测器
接受一个输入，做出预测，输出结果，称之为预测器。通过比较预测结果和真实值调整内部参数，可以使预测结果更加精确。下图为“千米转化为英里的预测器”：
<div align="center">
    <img src="static/pic/千米转化为英里的预测器.png" alt="千米转化为英里的预测器" width="50%">
</div>
$$英里=千米\times C$$
训练数据如下：

|真实示例|千米|英里|
| ---- | ---- | ---- |
|1|0|0|
|2|100|62.137|

让C=0.5；则，100千米=50英里；那么，误差值=真实值-计算值=62.137-50=12.137  
让C=0.6；则，100千米=60英里；那么，误差值=真实值-计算值=62.137-60=2.137  
让C=0.61；则，100千米=61英里；那么，误差值=真实值-计算值=62.137-61=1.137  
可以看出：  
误差值越小，C的调整就应该越小，可以将C的调整值取误差值的百分比。

#### 1.2 毛虫和瓢虫的分类器
下图中的直线可以将毛虫和瓢虫区分开来，可以用这条直线作为小虫的分类器。
<div align="center">
    <img src="static/pic/毛虫和瓢虫的分类器.png" alt="毛虫和瓢虫的分类器" width="50%">
</div>
这条直线可以写为  
$$y=Ax$$
训练数据如下:

|实例|宽度|长度|小虫|
|---|---|---|---|
|1|3.0|1.0|瓢虫|
|2|1.0|3.0|毛虫|

让A=0.25，则直线为$y=0.25x$，不能将小虫区分开来，如下图：
<div align="center">
    <img src="static/pic/毛虫和瓢虫的分类器1.png" alt="毛虫和瓢虫的分类器1" width="50%">
</div>

根据训练样本1，期望目标值设为1.1，避免直线穿过瓢虫；则，误差值=期望目标值-计算值=1.1-0.75=0.35，$\Delta A=0.35÷3=0.1167$；那么A=0.25+0.1167，直线为$y=0.3667x$。  
根据训练样本2，期望目标值设为2.9，避免直线穿过瓢虫；则，误差值=期望目标值-计算值=2.9-1*0.3667=2.5333，$\Delta A=2.5333÷1=2.5333$；那么A=0.3667+2.5333，直线为$y=2.9x$。  

如下图：
<div align="center">
    <img src="static/pic/毛虫和瓢虫的分类器2.png" alt="毛虫和瓢虫的分类器2" width="50%">
</div>
从上图可以看出，最终改进的直线抛弃了先前训练样本的学习结果，可以通过学习率（learning rate）来改进，让$A=A+L\Delta A$。  
设L=0.5，则三条直线分别为：y=0.25x，y=0.3083x，y=1.6042x，如下图：
<div align="center">
    <img src="static/pic/毛虫和瓢虫的分类器3.png" alt="毛虫和瓢虫的分类器2" width="50%">
</div>
