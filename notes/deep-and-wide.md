## 图神经网络无法做深
* 浅层网络极大的限制了图卷积网络的表达能力
* 由两个原因造成:
  * 过拟合 (Overfitting): 使用复杂模型去拟合少量数据的时候造成的泛化能力变差
  * 过平滑（Oversmoothing）: 在图神经网络消息传递过程中，所有节点的输入特征会收敛到一个和输入无关的子空间的过程。这一过程会导致输入GCN的特征失效并造成梯度消失
  
### 过平滑
* 添加残差连接/residual
* 借鉴DenseNet，将residual连接替换为dense连接
* 使用残差连接矫枉过正，残差模块完全忽略了相邻节点的权重
  
### DropEdge
* 随机删边技术

## 模型宽度
* 通过不同尺度感受野的组合对提高模型对节点的表征能力

### mixhop
* 表示邻居之间的特征的不同
* 高阶的信息传递
* 具体为表示两跳delta算子

## reference 
- 2018 | ICML | Representation Learning on Graphs with Jumping Knowledge Networks | Keyulu Xu et al.
- 2019 | ICCV | DeepGCNs: Can GCNs Go as Deep as CNNs? | Guohao Li, Matthias Müller et al.
- 2019 | KDD | Cluster-GCN: An Efficient Algorithm for Training Deep and Large Graph Convolutional Networks | Wei-Lin Chiang, Xuanqing Liu, Si Si, Yang Li, Samy Bengio and Cho-Jui Hsieh
- 2019 | ICML | MixHop: Higher-Order Graph Convolutional Architectures via Sparsified Neighborhood Mixing | Sami Abu-El-Haija, Bryan Perozzi et al. | [code](https://github.com/samihaija/mixhop)
- 2020 | ICLR | DropEdge: Towards Deep Graph Convolutional Networks on Node Classification | Yu Rong et al. | [code](https://github.com/DropEdge/DropEdge)
