# Binary Tree 二叉树
> By __uyiqgyy__
> _Apr 27th, 2017_
## 1.定义

1. 每个节点最多只有两个分支(不存在分支度大于2的节点)的树结构.
   - 路径 Path
   - 深度 Depth
   - 高度 Height
   - 节点 Node
   - 叶子 Leaf ： A __leaf__ node is any node that has two empty children.
   - An __internal__ node is any node that has at least one non-empty child.
2. 二叉树的第i层至多拥有<img src="http://chart.googleapis.com/chart?cht=tx&chl=$2^{i-1}$" style="border:none;">个节点数。（数学归纳法）
3. 深度为k的二叉树至多总共有<img src="http://chart.googleapis.com/chart?cht=tx&chl=$2^{k%2B1}-1$" style="border:none;">个节点数。（数学归纳法）
4. 对于任意一棵二叉树，n0 = 叶子结点总数，n1 = 度为1的结点总数，n2 = 度为2的结点总数，n 为总结点数.有结论:n0 = n2 + 1;
   1. 分支线总数 = n - 1;（数学归纳法）
   2. 分支线总数 = n1 + 2n2;
   2. n = n0 + n1 + n2; 
   3. n0 + n1 + n2 - 1 = n1 + 2n2 => n0 = n2 + 1;

### 满二叉树
* 国内教程定义：一个二叉树，如果每一个层的结点数都达到最大值，则这个二叉树就是满二叉树。也就是说，如果一个二叉树的层数为K，且结点总数是(2^k) -1 ，则它就是满二叉树。
* 国外(国际)定义:a binary tree T is full if each node is either a leaf orpossesses exactly two childnodes.
大意为：如果一棵二叉树的结点要么是叶子结点，要么它有两个孩子结点，这样的树就是满二叉树。
_有区别的_
* 满二叉树的深度：<img src="http://chart.googleapis.com/chart?cht=tx&chl=$\log^{2(n%2B1)}$" style="border:none;">
### 完全二叉树
若设二叉树的深度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，第 h 层所有的结点都连续集中在最左边，这就是完全二叉树。
* 完全二叉树的深度：向下取整数<img src="http://chart.googleapis.com/chart?cht=tx&chl=$\log^{2n}%2B1$" style="border:none;">
<img src="http://upload-images.jianshu.io/upload_images/1170656-5a5492bf84d52b72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
## 遍历
### 前序
最先读取根节点，然后再读取左子树（按照同样的方法读取子树上的节点），最后读取右子树。
### 中序
第二个读取根节点，最先要读取的是左子树，然后根节点，最后右子树。
### 后序
最后一个读取根节点，最先读取的是左子树，第二个读取右子树，最后读取根节点。
## 实现
### 二叉树
### 增加节点
### 遍历
## 广度遍历 & 深度遍历
## BST 
* 若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
* 若任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；
* 任意节点的左、右子树也分别为二叉查找树；
* 没有键值相等的节点。
## 霍夫曼树
## 平衡树
平衡二叉树——平衡二叉树又被称为AVL树（区别于AVL算法），它是一棵二叉排序树，且具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
## 红黑树
## 堆
### 堆排序算法
## Java 二叉树使用地方
* TreeSet,TreeMap都运用了红黑树。
* Java 8 中，HashMap在冲突数为8后，链表改用红黑树。

