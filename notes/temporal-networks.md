## temporal networks
* 为不同网络快照节点学习有用的时空特征低维表示
* GCN+LSTM
* 使用静态节点嵌入对算法进行初始化，然后将其在不同时间点的节点表示对齐

## 点过程模型
* DyRep
  * 两阶段：网络的动态(拓扑演化)和网络上的动态(节点之间的活动)
* HTNE
  * 基于霍克斯过程，捕获历史邻居对当前邻居的影响
  
## 注意力模型
* DySAT
  * 沿时间和空间两个维度共同采用自我注意层来计算节点表示


## reference
* 2018 | KDD | Embedding Temporal Network via Neighborhood Formation | Yuan Zuo et al.
* 2019 | ICLR | DyRep: Learning Representations over Dynamic Graphs | Rakshit Trivedi et al.
* 2019 | ICML | Dynamic Graph Representation Learning via Self-Attention Networks | Aravind Sankar et al.
* 2019 | IJCAI | Node Embedding over Temporal Graphs | Uriel Singer et al.
