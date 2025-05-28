# 实验4_实现智能图像分类 APP

## 一、实验内容

按照教程构建一个基于 **TensorFlow Lite** 的 Android 花卉识别应用。

查看应用的整体代码框架，特别关注以下两方面：

- **CameraX 库（`androidx.camera.\*`）** 的使用；
- **数据视图模型（ViewModel）** 的使用。

上传完成既定功能的代码至 **GitHub**，并撰写详细的 **README 文档**。

---

## 二、实验步骤

## 下载代码编译运行

1.先从https://github.com/hoitab/TFLClassify下载项目文件并且解压到Android studio项目文件中。安装教程编译运行并解决生成项目中的错误。

![image-20250514094144137](EX3_picture\image-20250514094144137.png)

## 向应用中添加[TensorFlow Lite](https://so.csdn.net/so/search?q=TensorFlow Lite&spm=1001.2101.3001.7020)

1.右键“start”模块，或者选择File，然后New>Other>TensorFlow Lite Model

<img src="EX4_picture\image-20250514095005476.png" alt="image-20250514095005476" style="zoom:50%;" />

2.选择已经下载的自定义的训练模型。本教程模型训练任务以后完成，这里选择finish模块中ml文件下的FlowerModel.tflite。

<img src="EX4_picture\image-20250514094938529.png" alt="image-20250514094938529" style="zoom:50%;" />

点击“Finish”完成模型导入，系统将自动下载模型的依赖包并将依赖项添加至模块的build.gradle文件。

3.最终TensorFlow Lite模型被成功导入，并生成摘要信息

![image-20250514095037524](EX4_picture\image-20250514095037524.png)

## 检查代码中的TODO项

本项目初始代码中包括了若干的TODO项，以导航项目中未完成之处。为了方便起见，首先查看TODO列表视图，View>Tool Windows>TODO

<img src="EX4_picture\image-20250514095339885.png" alt="image-20250514095339885" style="zoom: 50%;" />

![image-20250514095625996](EX4_picture\image-20250514095625996.png)

## 添加代码重新运行APP

1.定位“start”模块**MainActivity.kt**文件的TODO 1，添加初始化训练模型的代码

![image-20250514110202083](EX4_picture\image-20250514110202083.png)

2.在CameraX的analyze方法内部，需要将摄像头的输入`ImageProxy`转化为`Bitmap`对象，并进一步转化为`TensorImage` 对象

![image-20250514110402644](EX4_picture\image-20250514110402644.png)

3.对图像进行处理并生成结果，主要包含下述操作：

- 按照属性`score`对识别结果按照概率从高到低排序
- 列出最高k种可能的结果，k的结果由常量`MAX_RESULT_DISPLAY`定义

![image-20250514110430342](EX4_picture\image-20250514110430342.png)

4.将识别的结果加入数据对象`Recognition` 中，包含`label`和`score`两个元素。后续将用于`RecyclerView`的数据显示

![image-20250514110453862](EX4_picture\image-20250514110453862.png)

5.将原先用于虚拟显示识别结果的代码注释掉或者删除

![image-20250514110732472](EX4_picture\image-20250514110732472.png)

6.以物理设备重新运行start模块

7.最终运行效果

<img src="EX4_picture\1.jpg" alt="1" style="zoom:50%;" />