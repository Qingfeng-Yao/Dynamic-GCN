## 图卷积
- 将卷积拓展到图上
	- no node ordering: 当节点没有给定位置时，如何将template特征和数据特征进行匹配
	- heterogeneous neighborhood: 如何解决不同的邻域大小
- 将卷积定理扩展到图上
	- 如何定义图傅立叶变换
	- 如何在O(n)时间内计算快速谱卷积(for compact kernels)
- 谱卷积
	- 图拉普拉斯：谱图理论中的核心算子；`measure of smoothness`(局部值与邻域平均值之间的difference)；一个对图进行调和分析的算子
	- 傅立叶函数：图拉普拉斯的特征向量；图拉普拉斯的特征值/spectrum
	- 傅立叶变换：线性操作；将傅立叶变换迁移到图上的核心工作是把拉普拉斯算子的特征函数对应到图拉普拉斯的特征向量
	- 卷积定理
- 定义图上的template matching: 对于所有的邻居节点使用相同的template特征

## Neighborhood aggregation-based graph embedding methods
### Spectral methods/谱域图卷积
* Spectral network/vanilla spectral GCN
	* 限制：1)no guarantee of spatial localization of filter; 2)每一层要学O(n)个参数; 3)O(n^2)的学习复杂度(直接使用特征向量矩阵)
* SplineGCNs
	* smooth spectral filters/localized spatial filters(localization in space/smoothness in frequency domain)
	* K个smooth kernels B(splines)的线性组合
	* 特点：1)localized filters in space(fast-decaying); 2)每一层要学O(1)个参数; 3)O(n^2)的学习复杂度(直接使用特征向量矩阵)
* LapGCNs
	* 直接使用图拉普拉斯(每一次拉普拉斯操作以1 hop增加函数的support)
	* 特点：1)filters are exactly localized in k-hop supports; 2)每一层要学O(1)个参数; 3)学习复杂度：O(EK)=O(n) for sparse graphs; 4)不需要特征分解; 5)monomials basis are unstable under coefficients perturbation(hard to optimize)
* ChebNet
	* 引入切比雪夫多项式
	* 特点：1)filters are exactly localized in k-hop supports; 2)每一层要学O(1)个参数; 3)学习复杂度：O(EK)=O(n) for sparse graphs; 4)不需要特征分解; 5)stable under coefficients perturbation
* GCN

### Spatial methods/空域图卷积
* MoNet
* GraphSAGE 
* GAT

```
谱方法无法扩展到大图上，因此发展出空间方法。还有原因是谱方法中学习到的filters依赖于拉普拉斯特征基，而拉普拉斯特征基依赖于图结构，因此在特定结构上训练的模型不能直接应用于具有不同结构的图
空间方法是直接在图域上执行卷积
为了快速的图表示学习，几个基于采样的方法被提出
```

### Sampling-based methods
* GraphSAGE: node-wise sampling methods
* FastGCN: layer-wise approach
	* its layer-dependent variant

## GraphSage
* 学习一组聚合函数
	* 该函数通过从节点的局部邻域采样SAmple和聚合aggreGatE特征来生成嵌入
	* 对每个节点均匀采样一个固定大小的邻域，然后对其执行特定聚合器
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

## References
- 1997 | Spectral graph theory | F.R.K.Chung
- 2006 | A tutorial on spectral clustering | Luxburg
- 2011 | Wavelets on graphs via spectral graph theory | Hammond, Pierre Vandergheynst and Gribonval
- 2012 | The emerging field of signal processing on graphs: extending high-dimensional data analysis to networks and other irregular domains
- 2014 | ICLR | Spectral Networks and Locally Connected Networks on Graphs | Joan Bruna, Wojciech Zaremba, Arthur Szlam and Yann LeCun
- 2016 | ICML | Learning Convolutional Neural Networks for Graphs | Mathias Niepert et al.
- 2016 | ICLR | Gated Graph Sequence Neural Networks | Li et al. 
- 2016 | NIPS | Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering | Defferrard, Xavier Bresson and Pierre Vandergheynst | [code](https://github.com/mdeff/cnn_graph)
- 2017 | ICLR | Semi-Supervised Classification Graph Convolutional Networks | Thomas N. Kipf and Max Welling | [code](https://github.com/tkipf)
- 2017 | CVPR | Geometric Deep Learning on Graphs and Manifolds Using Mixture Model Cnns | Federico Monti et al.
- 2017 | NIPS | Inductive Representation Learning on Large Graphs | William L. Hamilton, Rex Ying and Jure Leskovec | [code](https://github.com/williamleif/graphsage-simple)
- 2017 | ICML | Neural Message Passing for Quantum Chemistry | Gilmer et al.
- 2018 | AAAI | Adaptive Graph Convolutional Neural Networks | Ruoyu Li et al.
- 2018 | ICLR | Graph Attention Networks | Velickovic et al. | [code](https://github.com/PetarV-/GAT)
- 2018 | KDD | Large-scale Learnable Graph Convolutional Networks | Hongyang Gao et al.
- 2018 | ICLR | FastGCN: Fast Learning with Graph Convolutional Networks via Importance Sampling | Chen et al. | [code](https://github.com/matenure/FastGCN)
- 2018 | NIPS | Adaptive Sampling Towards Fast Graph Representation Learning | Wenbing Huang et al.
