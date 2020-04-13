## Neighborhood aggregation-based graph embedding methods
### Spectral methods/谱域图卷积
* Spectral network 
* ChebNet
* GCN

### Spatial methods/空域图卷积
* MoNet
* GraphSAGE 
* GAT

```
谱方法无法扩展到大图上，因此发展出空间方法
空间方法是直接在图域上执行卷积
为了快速的图表示学习，几个基于采样的方法被提出
```

### Sampling-based methods
* GraphSAGE: node-wise sampling methods
* FastGCN: layer-wise approach
	* its layer-dependent variant

## Spectral network
* 基于谱图理论`spectral graph theory`发展图卷积`graph convolution`

## ChebNet
* K-局部化，只依赖于远离中心节点的最大K步的节点(K阶邻域)

## GCN
* 令`K=1`
* 将节点的邻域建模成接受场`receptive field`，然后应用图卷积算子(可看作是a center-surround filter in CNN)：邻居节点特征的加权和
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

## Reference
- 2014 | ICLR | Spectral Networks and Locally Connected Networks on Graphs | Joan Bruna, Wojciech Zaremba, Arthur Szlam and Yann LeCun
- 2016 | ICML | Learning Convolutional Neural Networks for Graphs | Mathias Niepert et al.
- 2016 | ICLR | Gated Graph Sequence Neural Networks | Li et al. 
- 2016 | NIPS | Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering | Defferrard, Xavier Bresson and Pierre Vandergheynst | [code](https://github.com/mdeff/cnn_graph)
- 2017 | ICLR | Semi-Supervised Classification Graph Convolutional Networks | Thomas N. Kipf and Max Welling | [code](https://github.com/tkipf)
- 2017 | CVPR | Geometric Deep Learning on Graphs and Manifolds Using Mixture Model Cnns | Federico Monti et al.
- 2017 | ICLR | Semi-Supervised Classification Graph Convolutional Networks | Thomas N. Kipf and Max Welling | [code](https://github.com/tkipf) 
- 2017 | NIPS | Inductive Representation Learning on Large Graphs | William L. Hamilton, Rex Ying and Jure Leskovec | [code](https://github.com/williamleif/graphsage-simple)
- 2017 | ICML | Neural Message Passing for Quantum Chemistry | Gilmer et al.
- 2018 | AAAI | Adaptive Graph Convolutional Neural Networks | Ruoyu Li et al.
- 2018 | ICLR | Graph Attention Networks | Velickovic et al. | [code](https://github.com/PetarV-/GAT)
- 2018 | KDD | Large-scale Learnable Graph Convolutional Networks | Hongyang Gao et al.
- 2018 | ICLR | FastGCN: Fast Learning with Graph Convolutional Networks via Importance Sampling | Chen et al. | [code](https://github.com/matenure/FastGCN)
- 2018 | NIPS | Adaptive Sampling Towards Fast Graph Representation Learning | Wenbing Huang et al.
