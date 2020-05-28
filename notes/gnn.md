## 分类
- RGNN
- CGNN
- graph autoencoders
- spatial-temporal GNN

## RGNN
- GNN的概念最初在Gori中概述过，并在Scarselli和Gallicchio中进一步阐述；这些早期的研究属于递归图神经网络（RecGNNs）的范畴
- 它们通过迭代传播邻域信息直到达到一个稳定的不动点stable fixed point来学习目标节点的表示
	- 假设图中的一个节点不断地与它的邻居交换信息/消息，直到达到一个稳定的平衡
- 基于空间的卷积图神经网络继承了信息传递的思想(Micheli)
	- 通过体系结构上复合的非递归层首次解决了图的相互依赖性
- 这个过程在计算上是昂贵的，在Li和Dai中克服这些挑战

## CGNN
- 主要想法是通过聚合节点本身的特征和邻居特征来生成节点表示，通过堆叠多层，每个节点最后的表示可以接受来自更远邻域的信息
- 与RecGNNs不同，ConvGNNs通过堆叠多个图卷积层来抽取高层次节点表示

## GAEs
- 无监督学习框架
	- 将节点/图编码进一个隐含向量空间，然后从编码信息中重建图数据
	- 用来学习图嵌入和图生成分布
		- 图嵌入：通过重建图的结构信息(如邻接矩阵)来学习隐含节点表示
		- 图生成分布

## STGNNs 
- 拓扑结构静止，点或边特征变化
- 主要思想：
	- 同时考虑空间相关性dependency和时间相关性
	- 目前许多方法利用图卷积捕获空间相关性，利用RNNs或CNNs建模时间相关性
- 应用：
	- traffic speed forecasting
	- driver maneuver anticipation
	- human action recognition

## Frameworks
- Node-level: 
	- 节点回归或节点分类任务
	- 多层感知机或softmax 
- Edge-level 
	- 边分类或连接预测任务
	- 以两个节点的隐含表示为输入，使用相似性函数或神经网络可预测边的标签或连接强度
- Graph-level 
	- 图分类任务
	- 池化操作或read-out操作

## Training Frameworks
- Semi-supervised learning for node-level classification[2] 
- Supervised learning for graph-level classification 
- Unsupervised learning for graph embedding
	- 这些算法以两种方式利用edge-level信息
		- 1、采用autoencoder框架
		- 2、负采样方法
			- 其中logistic regression层被用来区分正负配对


## References
- 2005 | A new model for learning in graph domains | Gori et al.
- 2009 | The graph neural network model | Scarselli et al.
- 2009 | Neural network for graphs: A contextual constructive approach | Micheli et al.
- 2010 | Graph echo state networks | Gallicchio et al.
- 2015 | ICLR | Gated graph sequence neural networks | Li et al.
- 2016 | NIPS | Variational graph auto-encoders | Kipf et al.
- 2016 | CVPR | Structural-rnn: Deep learning on spatio-temporal graphs | Jain et al.
- 2018 | IJCAI | Adversarially regularized graph autoencoder for graph embedding | Pan et al.
- 2018 | ICML | Learning steady-states of iterative algorithms over graphs | Dai et al.
- 2018 | ICLR | Diffusion convolutional recurrent neural network: Data-driven traffic forecasting | Li et al.
- 2018 | AAAI | Spatial temporal graph convolutional networks for skeleton-based action recognition | Yan et al.
- 2018 | IJCAI | Spatio-temporal graph convolutional networks: A deep learning framework for traffic forecasting | Yu et al.




