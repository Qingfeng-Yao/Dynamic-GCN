## citation networks

### three datasets
* Citeseer
	* 以下details的shape分别为`(2312，3703)`, `(120,3703)`, `(1000,3703)`, `(2312,6)`, `(120,6)`, `(1000,6)`
	* `graph`：3327个点，4732条边
	* 有孤立点: 测试索引从2312-3326，共1000个
* Cora
	* 以下details的shape分别为`(1708，1433)`, `(140,1433)`, `(1000,1433)`, `(1708,7)`, `(140,7)`, `(1000,7)`
	* `graph`：2708个点，5429条边
	* 测试索引从1708-2707，共1000个
* Pubmed
	* 以下details的shape分别为`(18717，500)`, `(60,500)`, `(1000,3)`, `(18717,3)`, `(60,3)`, `(1000,3)`
	* `graph`：19717个点，44338条边
	* 测试索引从18717-19716，共1000个

### details
* `allx`, `x`, `tx`: 特征向量-->csr矩阵
* `ally`, `y`, `ty`: one-hot标签-->numpy.ndarray
* `graph`: dict形如{index:[index of 邻居节点]}
* `test.index`

### reference
* 2008 | Collective Classification in Network Data | Sen et al.
* 2016 | ICML | Revisiting Semi-supervised Learning with Graph Embeddings | Yang et al.