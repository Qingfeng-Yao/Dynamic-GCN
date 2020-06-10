## dynamic networks/graphs
* 拥有时序和结构模式
* 分类(动态网络表示)(依据temporal granularity)
  * 离散时间动态图：一系列快照
  * 连续时间动态图：初始状态+观测/事件
* node dynamics
* link dynamics

## 动态网络模型
* 动态随机图: 随机图模型(RGM)和指数随机图模型(ERGM)是在遵循已知的网络拓扑结构的情况下产生随机连接图的随机图模型
* (生成)概率模型
  * 动态随机块模型：随机块模型在几千个节点上扩展到一个数量级更大的网络
  * 动态隐含空间模型：隐含空间模型需要用马尔可夫链蒙特卡罗(MCMC)方法来拟合参数，并且非常灵活，但只能扩展到几百个节点
* stochastic actor oriented models: SAOM是一种连续时间模型，将每个节点视作一个actor，并建模其行为。该模型学习表示网络结构、actor位置和actor行为之间的依赖关系
* 动态网络表示学习
  * 基于张量分解：类似矩阵分解，但多了时间维度
  * 基于随机游走：静态图基于随机游走嵌入方法的扩展或应用时序随机游走
  * 基于深度学习
    * temporal restricted Boltzmann machines：概率生成模型，应用于动态链接预测
    * 动态图神经网络：模型的离散版本(GNN+RNN/时间序列模型)；模型的连续版本(必须修改节点聚合的方式)
* relational event models: 用于交互网络的连续时间模型，定义了未来事件在节点对之间发生的倾向

## 动态图神经网络
### 离散模型
- Stacked DGNNs：独立的GNN处理每一个快照，然后将所有输出输入到时间序列模型
  - GCRN-M1：Seo
  - WD-GCN和CD-GCN：Manessi
- Integrated DGNNs：将GNN和RNN结合在一层
  - GCRN-M2：Seo
  - EvolveGCN：Aldo Pareja
  - DySAT 
- Dynamic graph autoencoders and generative models
  - DynGEM, Dyngraph2vec
  - GCN-GAN

### 连续模型
- RNN based models: 节点嵌入由基于RNN的框架维护；一旦网络发生变化，交互节点的嵌入就会更新
  - Streaming graph neural networks
  - JODIE
- Temporal point process based models: 时间点过程由神经网络参数化
  - DyREP: 两阶段，网络的动态(拓扑演化)和网络上的动态(节点之间的活动)
  - HTNE：基于霍克斯过程，捕获历史邻居对当前邻居的影响
  
## 注意力模型
* DySAT
  * 沿时间和空间两个维度共同采用自我注意层来计算节点表示
  
## 预测事件


## reference
* 2016 | Structured Sequence Modeling with Graph Convolutional Recurrent Networks | Seo et al.
* 2017 | Dynamic graph convolutional networks | Manessi et al.
* 2018 | KDD | Embedding Temporal Network via Neighborhood Formation | Yuan Zuo et al.
* 2018 | DynamicGEM: A library for dynamic graph embedding methods | Palash Goyal et al.
* 2018 | Streaming Graph Neural Networks | Yao Ma et al.
* 2019 | Dyngraph2vec: Capturing Network Dynamics using Dynamic Graph Representation Learning | Palash Goyal et al.
* 2019 | ICLR | DyRep: Learning Representations over Dynamic Graphs | Rakshit Trivedi et al.
* 2019 | ICML | Dynamic Graph Representation Learning via Self-Attention Networks | Aravind Sankar et al.
* 2019 | IJCAI | Node Embedding over Temporal Graphs | Uriel Singer et al.
* 2019 | KDD | Learning Dynamic Context Graphs for Predicting Social Events | Songgaojun Deng et al.
* 2019 | Evolvegcn: Evolving graph convolutional networks for dynamic graphs | Aldo Pareja et al.
* 2019 | Infocom | Gcn-gan: A non-linear temporal link prediction model for weighted dynamic networks | Kai Lei et al.
* 2019 | KDD | Predicting dynamic embedding trajectory in temporal interaction networks | Srijan Kumar, Xikun Zhang, and Jure Leskovec
* 2020 | Foundations and modelling of dynamic networks using Dynamic Graph Neural Networks: A survey | Joakim Skarding et al.
