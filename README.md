《基于标签感知图表示学习的多标签图像分类》框架图如下

![image](https://github.com/cyilu/introduction/blob/master/GRL_framework.png)

动机    ：1、词向量不能很好的表达多标签任务中的语义，应与标签共现结合（框架图）

          2、之前的工作中，语义解耦以词向量作为输入，并且将视觉特征和标签投影到共同的
              空间，效率和准确率都不高
              
主要贡献：1、性能超过两篇2019年顶会的文章

2、语义交互模块使用一个GNN（建立在标签共现上）挖掘标签的关系，生成标签表示
          
3、语义解耦采用标签表示作为输入，并follow Chen等人，将标签投影到视觉特征空间

4、语义解耦操作分离出label-wise视觉特征，用另一个GNN探索视觉特征的关系

5、采用一组相互独立的分类器用于分类

主要技术：1、Gated Graph Neural Networks

          2、分布式DistributedDataParallel
          
          3、混合精度计算apex
          
收获    ：经反复消融实验，发现影响性能的有以下几点：1、图片的插值函数；2、Batchsize；3、图片的扭曲增强；4、对于多块GPU，同步BatchNormalization；5、图片resize缩放的范围
