# Binary Tree 二叉树
> By __uyiqgyy__
> _Apr 27th, 2017_
## 定义
- 每个节点最多只有两个分支(不存在分支度大于2的节点)的树结构.
- 二叉树的第i层至多拥有<img src="http://chart.googleapis.com/chart?cht=tx&chl=$2^{i-1}$" style="border:none;">个节点数；深度为k的二叉树至多总共有<img src="http://chart.googleapis.com/chart?cht=tx&chl=$2^{k%2B1}-1$" style="border:none;">个节点数
路径 Path
深度 Depth
高度 Height
节点 Node
叶子 Leaf ： A __leaf__ node is any node that has two empty children.
An __internal__ node is any node that has at least one non-empty child. 
### 满二叉树
- 国内教程定义：一个二叉树，如果每一个层的结点数都达到最大值，则这个二叉树就是满二叉树。也就是说，如果一个二叉树的层数为K，且结点总数是(2^k) -1 ，则它就是满二叉树。
- 国外(国际)定义:a binary tree T is full if each node is either a leaf orpossesses exactly two childnodes.
大意为：如果一棵二叉树的结点要么是叶子结点，要么它有两个孩子结点，这样的树就是满二叉树。
_有区别的_
### 完全二叉树
若设二叉树的深度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，第 h 层所有的结点都连续集中在最左边，这就是完全二叉树。
## Node？ 深度？ 根，叶节点。
## 遍历
### 前序
### 中序
### 后序
## 实现
### 二叉树
### 增加节点
### 遍历
## 广度遍历 & 深度遍历
## BST 
- 若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
- 若任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；
- 任意节点的左、右子树也分别为二叉查找树；
- 没有键值相等的节点。
## 霍夫曼树
## 自平衡树
## 红黑树
## 堆
### 堆排序算法
## Java 二叉树使用地方
