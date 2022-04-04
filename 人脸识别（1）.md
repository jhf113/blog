### opencv介绍
1. opencv是intel在1999发起的，2000年贡献出来，willow garage公司在维护，开发了ROS机器人操作系统，开发beam远程协助机器人，国内有叫派宝
2. 除了opencv以外，还有那些图像处理开源软件：
   - OpenMV，基于stm32f4
   + SimpleCV，视觉框架，为用户提供一个更好的编程接口
   + SOD，主要应用在嵌入式，代码是开源免费的，训练好的模型要收费
   + Dlib是一个很有名的库了，有c++、Python的接口。使用dlib可以大大简化开发，比如人脸识别，特征点检测之类的工作都可以很轻松实现。同时也有很多基于dlib开发的应用和开源库，比如face_recogintion库
   + Halcon，商业的，比较贵

### dlib介绍

  dlib由davis King发起的，引入了ResNet残差神经网络，ResNet由何凯明提出的
 
1. 文档齐全

   不像很多其他的开源库一样，Dlib为每一个类和函数提供了完整的文档说明。同时，还提供了debug模式；打开debug模式后，用户可以调试代码，查看变量和对象的值，快速定位错误点。另外，Dlib还提供了大量的实例。

2. 高质量的可移植代码

      Dlib不依赖第三方库，无须安装和配置，这部分可参照（官网左侧树形目录的how to compile的介绍）。Dlib可用在window、Mac OS、Linux系统上。

3. 提供大量的机器学习 / 图像处理算法

 + 深度学习

 + 基于SVM的分类和递归算法

 + 针对大规模分类和递归的降维方法

 + 相关向量机(relevance vector machine)；是与支持向量机相同的函数形式稀疏概率模型，对未知函数进行预测或分类。其训练是在贝叶斯框架下进行的，与SVM相比，不需要估计正则化参数，其核函数也不需要满足Mercer条件，需要更少的相关向量，训练时间长，测试时间短。

 + 聚类： linear or kernel k-means, Chinese Whispers, and Newman clustering. Radial Basis Function Networks

 + 多层感知机
