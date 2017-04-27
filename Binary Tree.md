# Binary Tree 二叉树
> By __uyiqgyy__
> _Apr 27th, 2017_
* [1. 定义](#1)
## 1.定义 <a name = "1"/>
1. 每个节点最多只有两个分支(不存在分支度大于2的节点)的树结构.
   - 路径 Path
   - 深度 Depth
   - 层 Level
   - 高度 Height
   - 节点 Node
   - 叶子 Leaf ： A __leaf__ node is any node that has two empty children.
   - An __internal__ node is any node that has at least one non-empty child.
2. 二叉树的第i层至多拥有<img src="http://chart.googleapis.com/chart?cht=tx&chl=$2^{i-1}$" style="border:none;">个节点数。（数学归纳法）
3. 深度为k的二叉树至多总共有<img src="http://chart.googleapis.com/chart?cht=tx&chl=$2^{k%2B1}-1$" style="border:none;">个节点数。(数学归纳法)
4. 对于任意一棵二叉树，n0 = 叶子结点总数，n1 = 度为1的结点总数，n2 = 度为2的结点总数，n 为总结点数.有结论:n0 = n2 + 1;
   1. 分支线总数 = n - 1;（数学归纳法）
   2. 分支线总数 = n1 + 2n2;
   3. n = n0 + n1 + n2; 
   4. n0 + n1 + n2 - 1 = n1 + 2n2 => n0 = n2 + 1;
5. 如果对一棵有 n 个结点的完全二叉树(其深度为<img src="http://chart.googleapis.com/chart?cht=tx&chl=$[\log^{2n}]%2B1$" style="border:none;">的结点按层序编号(从第1层到第<img src="http://chart.googleapis.com/chart?cht=tx&chl=$[\log^{2n}]%2B1$" style="border:none;">层,每一层从左到右),对任一结点i (1 <= i <= n) 有:
   1. 如果 i = 1 ,则结点i是二叉树的根,无双亲;如果i > 1,则其双亲是结点 [ i /2 ];
   2. 如果 2i > n,则结点i无左孩子(结点i为叶子结点);否则其左孩子是结点2i;
   3. 如果 2i +1 > n,则结点i无右孩子;否则其右孩子是结点2i +1;

### 1.1 满二叉树
* 国内教程定义：一个二叉树，如果每一个层的结点数都达到最大值，则这个二叉树就是满二叉树。也就是说，如果一个二叉树的层数为K，且结点总数是(2^k) -1 ，则它就是满二叉树。
* 国外(国际)定义:a binary tree T is full if each node is either a leaf orpossesses exactly two childnodes.
大意为：如果一棵二叉树的结点要么是叶子结点，要么它有两个孩子结点，这样的树就是满二叉树。
_有区别的_
* 满二叉树的深度：<img src="http://chart.googleapis.com/chart?cht=tx&chl=$\log^{2(n%2B1)}$" style="border:none;">
### 1.2 完全二叉树
若设二叉树的深度为h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，第 h 层所有的结点都连续集中在最左边，这就是完全二叉树。
* 完全二叉树的深度：向下取整数<img src="http://chart.googleapis.com/chart?cht=tx&chl=$\log^{2n}%2B1$" style="border:none;">
* <img src="http://upload-images.jianshu.io/upload_images/1170656-5a5492bf84d52b72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
## 2. 存储方式
### 2.1 顺序存储
* <img src="http://7xirg5.com1.z0.glb.clouddn.com/binary-tree-arr.png">
* 因为完全二叉树有以上这些规则和特点，所以我们在日常使用中尽量使用完全二叉树，存储方式最好选择顺序存储；
### 2.2 链式存储
* 方便新增，删除操作；结构为数据域+左孩子指针+右孩子指针 （二叉链表），如果有必要的情况下可以添加双亲指针，指向结点的双亲（三叉链表），这都是根据业务需求_灵活控制_的
* <img src="http://7xirg5.com1.z0.glb.clouddn.com/binary-tree-lian.png">
## 3. 遍历
### 3.1 前序
* 最先读取根节点，然后再读取左子树（按照同样的方法读取子树上的节点），最后读取右子树。
* <img src="http://upload-images.jianshu.io/upload_images/1396375-9cd286f6ee54aae2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
### 3.2 中序
* 第二个读取根节点，最先要读取的是左子树，然后根节点，最后右子树。
* <img src="http://upload-images.jianshu.io/upload_images/1396375-21b62af4c49f03c1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
### 3.3 后序
* 最后一个读取根节点，最先读取的是左子树，第二个读取右子树，最后读取根节点。
* <img src="http://upload-images.jianshu.io/upload_images/1396375-f929b5b8ae27e10d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
### 3.4 广度遍历 & 深度遍历
## 4. BST 
* 若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
* 若任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；
* 任意节点的左、右子树也分别为二叉查找树；
* 没有键值相等的节点。
## 5. 霍夫曼树
## 6. 平衡树
* 平衡二叉树——平衡二叉树又被称为AVL树（区别于AVL算法），它是一棵二叉排序树，且具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
## 7. 红黑树
## 8. 二叉堆
### 8.1 堆排序算法
## 9. Java 二叉树使用地方
* TreeSet,TreeMap都运用了红黑树。
* Java 8 中，HashMap在冲突数为8后，链表改用红黑树。

