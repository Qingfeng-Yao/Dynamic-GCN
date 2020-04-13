## GCN无法做深
* 动机：深度CNN在图像分类上的成功
* 浅层网络极大的限制了图卷积网络的表达能力
* 由两个原因造成:
  * 过拟合 (Overfitting): 使用复杂模型去拟合少量数据的时候造成的泛化能力变差
  * 过平滑（Oversmoothing）: 在网络变深过程中，同一连通分量里的所有节点的特征会收敛到一个固定点(Oono & Suzuki (2019)：收敛到一个子空间)。这一过程会导致输入GCN的特征失效并造成梯度消失
  
### 过平滑
* 添加残差连接/residual: ResGCN
* 使用个性化PageRank，该PageRank还将根节点包含到消息传递循环中
* 借鉴DenseNet，将residual连接替换为dense连接: JKNet
 * 多跳消息传递
* DeepGCNs: 包含residual layers, dense connections and dilated convolutions
 * graph-level classification
* 使用残差连接矫枉过正，残差模块完全忽略了相邻节点的权重
  
### DropEdge
* 在每次训练epoch中随机删除输入图中的一部分边
 * 防止过拟合：数据增强(产生输入数据的不同随机变形)
   * 在训练期间采用随机子集聚合而非完全聚合
 * 防止过平滑：降低过平滑的收敛速度；减少过平滑导致的信息损失

## 模型宽度
* 通过不同尺度感受野的组合对提高模型对节点的表征能力

### mixhop
* 表示邻居之间的特征的不同
* 高阶的信息传递
* 具体为表示两跳delta算子

## 模型的表达能力
* 图同构测试/Weisfeiler-Leman

## reference 
- 2018 | AAAI | Deeper Insights into Graph Convolutional Networks for Semi-supervised Learning | Qimai Li et al.
- 2018 | ICML | Representation Learning on Graphs with Jumping Knowledge Networks | Keyulu Xu et al.
- 2019 | ICCV | DeepGCNs: Can GCNs Go as Deep as CNNs? | Guohao Li, Matthias Müller et al.
- 2019 | KDD | Cluster-GCN: An Efficient Algorithm for Training Deep and Large Graph Convolutional Networks | Wei-Lin Chiang, Xuanqing Liu, Si Si, Yang Li, Samy Bengio and Cho-Jui Hsieh
- 2019 | ICLR | Predict Then Propagate: Graph Neural Networks Meet Personalized Pagerank | Johannes Klicpera et al.
- 2019 | ICML | MixHop: Higher-Order Graph Convolutional Architectures via Sparsified Neighborhood Mixing | Sami Abu-El-Haija, Bryan Perozzi et al. | [code](https://github.com/samihaija/mixhop)
- 2019 | ICLR | How Powerful are Graph Neural Networks? | xukeyulu et al.
- 2020 | ICLR | Graph Neural Networks Exponentially Lose Expressive Power for Node Classification | Kenta Oono and Taiji Suzuki
- 2020 | ICLR | DropEdge: Towards Deep Graph Convolutional Networks on Node Classification | Yu Rong et al. | [code](https://github.com/DropEdge/DropEdge)
