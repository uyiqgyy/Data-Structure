# Binary Tree 二叉树
> By __uyiqgyy__
> _Apr 27th, 2017_
* [1. 定义](#1)
* [2. 存储方式](#2)
* [3. 遍历](#3)
* [4. BST](#4)
* [5. 霍夫曼树](#5)
* [6. 平衡树](#6)
* [7. 二叉堆](#7)
* [8. Java里的二叉树](#8)

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
## 2. 存储方式<a name="2"/>
### 2.1 顺序存储
* <img src="http://7xirg5.com1.z0.glb.clouddn.com/binary-tree-arr.png">
* 因为完全二叉树有以上这些规则和特点，所以我们在日常使用中尽量使用完全二叉树，存储方式最好选择顺序存储；
### 2.2 链式存储
* 方便新增，删除操作；结构为数据域+左孩子指针+右孩子指针 （二叉链表），如果有必要的情况下可以添加双亲指针，指向结点的双亲（三叉链表），这都是根据业务需求_灵活控制_的
* <img src="http://7xirg5.com1.z0.glb.clouddn.com/binary-tree-lian.png">
## 3. 遍历<a name="3"/>
### 3.1 前序
* 最先读取根节点，然后再读取左子树（按照同样的方法读取子树上的节点），最后读取右子树。
* <img src="http://upload-images.jianshu.io/upload_images/1396375-9cd286f6ee54aae2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
``` c++
//前序遍历
void preorder(TreeNode *root, vector<int> &path)
{
    if(root != NULL)
    {
        path.push_back(root->val);
        preorder(root->left, path);
        preorder(root->right, path);
    }
}
```
### 3.2 中序
* 第二个读取根节点，最先要读取的是左子树，然后根节点，最后右子树。
* <img src="http://upload-images.jianshu.io/upload_images/1396375-21b62af4c49f03c1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
``` c++
//中序遍历
void inorder(TreeNode *root, vector<int> &path)
{
    if(root != NULL)
    {
        inorder(root->left, path);
        path.push_back(root->val);
        inorder(root->right, path);
    }
}
```
### 3.3 后序
* 最后一个读取根节点，最先读取的是左子树，第二个读取右子树，最后读取根节点。
* <img src="http://upload-images.jianshu.io/upload_images/1396375-f929b5b8ae27e10d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240">
``` c++
//后续遍历
void postorder(TreeNode *root, vector<int> &path)
{
    if(root != NULL)
    {
        postorder(root->left, path);
        postorder(root->right, path);
        path.push_back(root->val);
    }
}
```
### 构造二叉树
* 前序＋中序
* 后序＋中序
### 3.4 广度优先遍历 & 深度优先遍历
1. 深度优先遍历: 深度优先遍历，从初始访问结点出发，我们知道初始访问结点可能有多个邻接结点，深度优先遍历的策略就是首先访问第一个邻接结点，然后再以这个被访问的邻接结点作为初始结点，访问它的第一个邻接结点。总结起来可以这样说：每次都在访问完当前结点后首先访问当前结点的第一个邻接结点。
   1. 访问初始结点v，并标记结点v为已访问。
   2. 查找结点v的第一个邻接结点w。
   3. 若w存在，则继续执行4，否则算法结束。
   4. 若w未被访问，对w进行深度优先遍历递归（即把w当做另一个v，然后进行步骤123）。
   5. 查找结点v的w邻接结点的下一个邻接结点，转到步骤3。
> 例如下图，其深度优先遍历顺序为 1->2->4->8->5->3->6->7
> <img src="https://segmentfault.com/img/bVlqSk">
2. 广度优先遍历: 类似于一个分层搜索的过程，广度优先遍历需要使用一个队列以保持访问过的结点的顺序，以便按这个顺序来访问这些结点的邻接结点。
   访问初始结点v并标记结点v为已访问。
   1. 结点v入队列
   2. 当队列非空时，继续执行，否则算法结束。
   3. 出队列，取得队头结点u。
   4. 查找结点u的第一个邻接结点w。
   5. 若结点u的邻接结点w不存在，则转到步骤3；否则循环执行以下三个步骤：
     1. 若结点w尚未被访问，则访问结点w并标记为已访问。
     2. 结点w入队列
     3. 查找结点u的继w邻接结点后的下一个邻接结点w，转到步骤6。
>（1）首先把二叉树的根节点送入队列； 
>（2）队首的节点出队列并访问之，然后把它的右子节点和左子节点分别入队列； 
>（3）重复上面两步操作，直至队空。
> 如下图，其广度优先算法的遍历顺序为：1->2->3->4->5->6->7->8
> <img src="https://segmentfault.com/img/bVlqSk">

## 4. BST <a name="4"/>
1. 性质
   * 若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
   * 若任意节点的右子树不空，则右子树上所有结点的值均大于等于它的根结点的值；
   * 任意节点的左、右子树也分别为二叉查找树；
2. 优点
   * 查找、插入的时间复杂度较低。为**O(log n)**
   * 最坏 O(n)（数列有序，树退化成线性表）
## 5. 霍夫曼编码树<a name="5"/>
*　给定n个权值作为n个叶子结点，构造一棵二叉树，若带权路径长度达到最小，称这样的二叉树为最优二叉树，也称为哈夫曼树(Huffman Tree)。哈夫曼树是带权路径长度最短的树，权值较大的结点离根较近。
### 5.1 构造
* 假设有n个权值，则构造出的哈夫曼树有n个叶子结点。 n个权值分别设为 w1、w2、…、wn，则哈夫曼树的构造规则为：
   1. 将w1、w2、…，wn看成是有n 棵树的森林(每棵树仅有一个结点)；
   2. 在森林中选出两个根结点的权值最小的树合并，作为一棵新树的左、右子树，且新树的根结点权值为其左、右子树根结点权值之和；
   3. 从森林中删除选取的两棵树，并将新树加入森林；
   4. 重复(2)、(3)步，直到森林中只剩一棵树为止，该树即为所求得的哈夫曼树。
### 5.2 原理
* 哈夫曼树的应用很广，哈夫曼编码就是其在电讯通信中的应用之一。广泛地用于数据文件压缩的十分有效的编码方法。其压缩率通常在20%～90%之间。在电讯通信业务中，通常用二进制编码来表示字母或其他字符，并用这样的编码来表示字符序列。 
* 例：如果需传送的电文为 ‘ABACCDA’，它只用到四种字符，用两位二进制编码便可分辨。假设 A, B, C, D 的编码分别为 00, 01,10, 11，则上述电文便为 ‘00010010101100’（共 14 位），译码员按两位进行分组译码，便可恢复原来的电文。
* 能否使编码总长度更短呢？
> 实际应用中各字符的出现频度不相同，用短（长）编码表示频率大（小）的字符，使得编码序列的总长度最小，使所需总空间量最少
* 数据的最小冗余编码问题
> 在上例中，若假设 A, B, C, D 的编码分别为 0，00，1，01，则电文 ‘ABACCDA’ 便为 ‘000011010’（共 9 位），但此编码存在多义性：可译为： ‘BBCCDA’、‘ABACCDA’、‘AAAACCACA’ 等。
* 译码的惟一性问题
> 要求任一字符的编码都不能是另一字符编码的前缀，这种编码称为前缀编码（其实是非前缀码）。 在编码过程要考虑两个问题，数据的最小冗余编码问题，译码的惟一性问题，利用最优二叉树可以很好地解决上述两个问题
### ５.3 例1：编码
* 如果需传送的电文为 ‘ABCACCDAEAE’，即：A, B, C, D, E 的频率（即权值）分别为0.36, 0.1, 0.27, 0.1, 0.18，试构造哈夫曼编码。
* <img src="http://images.cnitblog.com/blog2015/682679/201504/071119483365384.png">
* 编码： A：11，C：10，E：00，B：010，D：011 ，则电文 ‘ABCACCDAEAE’ 便为 ‘110101011101001111001100’（共 24 位，比 33 位短）。
### 5.4 例2:　译码
* 从哈夫曼树根开始，对待译码电文逐位取码。若编码是“0”，则向左走；若编码是“1”，则向右走，一旦到达叶子结点，则译出一个字符；再重新从根出发，直到电文结束。
* <img src="http://images.cnitblog.com/blog2015/682679/201504/071120393525832.png">
* 电文为 “1101000” ，译文只能是“CAT”
## 6. 平衡树<a name="6"/>
* 平衡二叉树——平衡二叉树又被称为AVL树（区别于AVL算法），它是一棵二叉排序树，且具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
### 6.1 红黑树
* 可以在**O(log n)**时间内做查找，插入和删除，这里的n是树中元素的数目
* 性质
   1. 节点是红色或黑色。
   2. 根是黑色。
   3. 所有叶子都是黑色（叶子是NIL节点）。
   4. 每个红色节点必须有两个黑色的子节点。（从每个叶子到根的所有路径上不能有两个连续的红色节点。）
   5. 从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点。
## 7. 二叉堆<a name="7"/>
### 7.1 堆排序算法
* ……
## 8. Java 二叉树使用地方<a name="8"/>
* TreeSet,TreeMap都运用了红黑树。
* Java 8 中，HashMap在冲突数为8后，链表改用红黑树。

