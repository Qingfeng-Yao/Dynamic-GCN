## dynamic networks/graphs
* 拥有时序和结构模式
* 分类(动态网络表示)(依据temporal granularity)
  * 离散时间动态图：一系列快照
  * 连续时间动态图：初始状态+观测/事件
* node dynamics
* link dynamics

## 动态网络模型
* 动态随机图: 随机图模型(RGM)和指数随机图模型(ERGM)是在遵循已知的网络拓扑结构的情况下产生随机连接图的随机图模型
* 概率模型
  * 动态随机块模型
  * 动态隐含空间模型
* stochastic actor oriented models: SAOM是一种连续时间模型，将每个节点视作一个actor，并建模其行为。该模型学习表示网络结构、actor位置和actor行为之间的依赖关系
* 动态网络表示学习
  * 基于张量分解
  * 基于随机游走
  * 基于深度学习
    * temporal restricted Boltzmann machines
    * 动态图神经网络：GNN+RNN
* relational event models: 用于交互网络的连续时间模型，定义了未来事件在节点对之间发生的倾向

## 点过程模型
* DyRep
  * 两阶段：网络的动态(拓扑演化)和网络上的动态(节点之间的活动)
* HTNE
  * 基于霍克斯过程，捕获历史邻居对当前邻居的影响
  
## 注意力模型
* DySAT
  * 沿时间和空间两个维度共同采用自我注意层来计算节点表示
  
## 预测事件


## reference
* 2018 | KDD | Embedding Temporal Network via Neighborhood Formation | Yuan Zuo et al.
* 2019 | ICLR | DyRep: Learning Representations over Dynamic Graphs | Rakshit Trivedi et al.
* 2019 | ICML | Dynamic Graph Representation Learning via Self-Attention Networks | Aravind Sankar et al.
* 2019 | IJCAI | Node Embedding over Temporal Graphs | Uriel Singer et al.
* 2019 | KDD | Learning Dynamic Context Graphs for Predicting Social Events | Songgaojun Deng et al.
* 2020 | Foundations and modelling of dynamic networks using Dynamic Graph Neural Networks: A survey | Joakim Skarding et al.
