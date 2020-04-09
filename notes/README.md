## Neighborhood aggregation-based graph embedding methods
### Spectral methods
* Spectral network 
* ChebNet
* GCN

### Spatial methods 
* MoNet
* GraphSAGE 
* GAT

## ChebNet
* K-局部化，只依赖于远离中心节点的最大K步的节点(K阶邻域)

## GCN
* 令`K=1`
* 将节点的邻域建模成接受场`receptive field`，然后应用图卷积`graph convolution`算子(可看作是a center-surround filter in CNN)
* 模型训练：端到端训练(有监督任务)-->定义一个关于节点嵌入输出的损失函数
* 所有节点共享参数；且允许新节点的归纳学习

## GraphSage
* 一般化聚合函数：任何可微函数(将一组向量映射为一个向量)
* 三个variants
  * Mean
  * Pool
  * LSTM
* concatenate self embedding and neighbor embedding 

## Gated Graph Neural Networks
* parameter sharing across layers(聚合函数不依赖于k)
* neighborhood aggregation with recurrent state update(使用RNN module)
* 可以处理超过20层的模型
* useful for complex networks representing

## Message-Passing Neural Networks
* 一般化gated graph neural network idea
	* generic "message" 函数，如sum或MLP
	* generic 更新函数，如LSTM或GRU
* 可包括边的特征
	* 主要用来解决边上有权重的图神经网络该如何更新Embedding的问题
	* 其中边上的权重被显式的建模到模型中来，作为邻居加权求和的权重，这里免去了对邻居权重的学习，直接用边的权重表征邻居的相对重要性



