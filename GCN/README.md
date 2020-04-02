## GCN
* 可被看成传统谱图方法的简化
* 将节点的邻域建模成接受场`receptive field`，然后应用图卷积`graph convolution`算子(可看作是a center-surround filter in CNN)
* 模型训练：端到端训练(有监督任务)-->定义一个关于节点嵌入输出的损失函数
* 所有节点共享参数；且允许新节点的归纳学习
