# 机器学习

## 内容与核心

+ 监督学习
1. 线性模型
2. 线性和二次判别分析
3. 核岭回归
4. 支持向量机
5. 随机梯度下降
6. 最近邻
7. 高斯过程
8. 交叉分解
9. 朴素贝叶斯
10. 决策树
11. 集成：梯度提升、随机森林、bagging、投票、stacking
12. 多类和多输出算法
13. 特征选择
14. 半监督学习
15. 等渗回归
16. 概率校准
17. 神经网络模型（监督）


+ 无监督学习
1. 高斯混合模型
2. 流形学习
3. 聚类
4. 双聚类
5. 信号分解（矩阵分解问题）
6. 协方差估计
7. 新颖性和异常值检测
8. 密度估计
9. 神经网络模型（无监督）



## 一 监督模型

### 1.线性模型

+ 普通最小二乘法
+ 非负最小二乘法
+ 普通最小二乘复杂度
+ 岭回归和分类
+ 套索
+ 多任务套索
+ 弹性网络
+ 多任务弹性网络
+ 最小角回归
+ LARS 套索
+ 正交匹配追踪（OMP）
+ 贝叶斯回归
+ 逻辑回归
+ 广义线性模型
+ 随机梯度下降 - SGD
+ 感知器
+ 被动攻击算法
+ 稳健性回归：异常值和建模误差
+ 分位数回归
+ 多项式回归：利用基函数扩展线性模型

线性模型通过以下方式扩展核心思想：
1. 正则化：控制过拟合（L1/L2正则化）。
2. 优化算法：适应不同场景（闭式解、梯度下降、LARS）。
3. 概率框架：贝叶斯方法引入不确定性。
4. 损失函数：适应不同任务（均方误差、Log损失、Huber损失）。
5. 非线性扩展：多项式回归、基函数扩展（如径向基函数）。

#### 什么是线性模型？

####




## 1 机器学习基本概念
机器学习模型分为
+ 有监督学习模型
+ 无监督学习模型

###  1.1 有监督学习模型
有监督学习模型主要分为**单模型**和**集成学习**两种：
+ **单模型**使用一个独立算法处理数据来学习和预测。其特点为简单易懂，训练和预测过程透明，计算开销小、训练时间短，且易于调试定位问题。不过，它易受数据噪声和异常值影响。
+ **集成学习**则结合多个模型提升预测性能，增强鲁棒性。其优势在于能综合各模型长处，性能通常优于单模型，对噪声和异常值耐受性更好。但它也存在不足，实现与调试复杂，需管理多个模型及组合方式，训练和预测消耗更多计算资源与时间。

#### 1.1.1 单模型
- **线性模型**：
    - **线性回归**：用于建立因变量和自变量之间的线性关系，通过最小化误差平方和来确定模型参数，常用于预测数值型结果。
    - **逻辑回归**：虽名字有“回归”，实则用于分类问题，利用对数几率函数将线性回归结果转化为概率值，判断样本所属类别。 
    - **Lasso**：在回归分析中引入L1正则化，可对系数进行压缩，实现特征选择和防止过拟合。
    - **Ridge**：即岭回归，引入L2正则化，在回归系数估计中加入惩罚项，使系数估计更稳定，降低方差。 
- **k近邻**：基于实例的学习方法，给定测试样本，通过计算与训练集中样本的距离（如欧氏距离），找出k个最近邻样本，根据这些样本的类别（分类问题）或数值（回归问题）来预测测试样本的结果。 

- **决策树**：
    - **ID3**：以信息增益为准则选择划分属性构建决策树，每次选择使信息增益最大的属性进行分裂。
    - **C5.0**：在ID3基础上改进，使用信息增益比，还能处理连续属性和缺失值，可生成规则集。 
    - **CART**：分类回归树，既能用于分类（二叉树，基于基尼指数选择划分属性 ），也能用于回归（基于最小平方误差 ）。 
- **神经网络**：
    - **感知机**：最简单的神经网络模型，由输入层、输出层组成，通过权重调整学习输入和输出的映射关系，可解决线性可分问题。 
    - **神经网络**：通常指多层感知机，包含多个隐藏层，能学习复杂的非线性映射关系，通过反向传播算法更新权重。 
- **支持向量机**：
    - **线性可分**：在样本线性可分情况下，寻找能最大化样本间隔的超平面进行分类。 
    - **线性支持**：针对近似线性可分情况，引入松弛变量允许部分样本出错。 
    - **线性不可分**：通过核函数将样本映射到高维空间，使其线性可分，再寻找最优超平面。 

#### 1.1.2 集成学习
- **Boosting**：
    - **GBDT**：梯度提升决策树，基于梯度下降思想，每次迭代拟合残差的近似值（负梯度 ），不断构建新决策树来提升模型性能。 
    - **AdaBoost**：通过改变样本权重，让后续弱学习器更关注之前被误分类的样本，迭代训练多个弱学习器并加权组合成强学习器。 
    - **XGBoost**：对GBDT的优化，在目标函数中加入正则项控制模型复杂度，支持并行计算，训练效率高，广泛应用于数据挖掘竞赛等领域。 
    - **LightGBM**：采用直方图算法等优化策略，减少内存占用和计算量，支持更快的并行学习，在处理大规模数据时表现出色。 
    - **CatBoost**：能自动处理类别型特征，采用排序提升算法，减少梯度估计偏差，在准确性和鲁棒性方面有不错表现。 
- **Bagging**：
    - **随机森林**：基于Bagging集成学习方法，从原始训练集有放回抽样构建多个子集，每个子集训练一棵决策树，最终通过对多棵树的预测结果进行投票（分类）或平均（回归）得到最终结果，能有效降低方差，防止过拟合。 


### 1.2 无监督学习模型
**无监督学习模型中的两个主要类别：聚类和降维。**


#### 1.2.1 聚类
+ 聚类: 是一种无监督学习技术，用于将数据集中相似的数据点分组。
  + K-means: 一种基于质心的聚类算法，通过迭代优化质心位置以最小化每个点到其所在簇中心的距离。
  + 层次聚类: 创建层次关系的聚类方法，可分为自底向上的聚合层次聚类和自顶向下的分裂层次聚类。
  + 谱聚类: 利用图论、通过计算数据点之间的相似度矩阵以进行聚类的方法。

#### 1.2.2  降维
+ 降维: 是无监督学习中的另一种方法，用于减少数据集的特征维数，同时尽量保留数据的主要信息。
  + PCA (主成分分析): 通过线性变换将数据映射到新的坐标系中，新坐标系的轴（主成分）按数据方差大小排序，以保留最大方差信息。
  + SVD (奇异值分解): 一种矩阵因子分解技术，常用于数据降维和压缩。
  + LDA (线性判别分析): 尽管通常用作监督学习，其思路也被用作降维技术，通过最大化类间分隔和最小化类内分布。


### 1.3 什么是监督学习？什么是非监督学习？
**所有的回归算法和分类算法都属于监督学习。并且明确的给给出初始值，在训练集中有特征和标签，并且通过训练获得一个模型，在面对只有特征而没有标签的数据时，能进行预测。**


+ **监督学习**：通过已有的一部分输入数据与输出数据之间的对应关系，生成一个函数，将输入映射到合适的输出，例如 分类。
+ **非监督学习**：直接对输入数据集进行建模，例如强化学习、K-means 聚类、自编码、受限波尔兹曼机。
+ **半监督学习**：综合利用有类标的数据和没有类标的数据，来生成合适的分类函数。






### 1.4 分类，回归和聚类

以下是重新制作的表格，更加清晰有序。您可以根据需要进一步调整格式：

|        分类       |                                定义                                |                       算法                       |         案例          |
|:---------------:|:------------------------------------------------------------------:|:-------------------------------------------------:|:---------------------:|
|      **分类**     |         对离散随机变量进行建模预测的监督学习                      |  LR, SVM, KNN, 决策树, 随机森林, GBDT            |      垃圾邮件分类     |
|      **回归**     |       对连续随机变量进行建模预测的监督学习                       |  非线性回归, SVR (支持向量回归->可用径向基核 (RBF)), 随机森林 |      房价预测        |
|      **聚类**     |         基于数据的内部规律，寻找其属于不同族群的无监督学习  |  Kmeans, 层次聚类, GMM (高斯混合模型)            |                     |




### 1.5 生成模式 vs 判别模式


## 2.线性模型

### 2.1 线性回归

**原理**: 用线性函数拟合数据，用 MSE（均方差） 计算损失，然后用梯度下降法(GD)找到一组使 MSE 最小的权重。


#### 2.1.1 什么是回归？哪些模型可用于解决回归问题？

**指分析因变量和自变量之间关系**

+ 线性回归: 对异常值非常敏感
+ 多项式回归: 如果指数选择不当，容易过拟合。
+ 岭回归
+ Lasso回归
+ 弹性网络回归

#### 2.1.2 线性回归的损失函数为什么是均方差?



#### 2.1.3 什么是线性回归？什么时候使用它？

利用最小二乘函数对一个或多个自变量和因变量之间关系进行建模的一种回归分析.
+ 自变量与因变量呈直线关系;
+ 因变量符合正态分布;
+ 因变量数值之间独立;
+ 方差是否齐性。



**最小二乘和均方误差之间的关系**

![alt text](image.png)


#### 2.1.4什么是梯度下降？SGD的推导？


#### 2.1.5什么是最小二乘法（最小平方法）？



#### 2.1.6 常见的损失函数有哪些？
1. 0-1损失  
2. 均方差损失(MSE)  
3. 平均绝对误差(MAE)   
4. 分位数损失(Quantile Loss)
分位数回归可以通过给定不同的分位点，拟合目标值的不同分位数；  
实现了分别用不同的系数控制高估和低估的损失，进而实现分位数回归。   
5. 交叉熵损失
6. 合页损失
一种二分类损失函数，SVM的损失函数本质： Hinge Loss + L2 正则化   
合页损失的公式如下：
![alt text](image-1.png)


#### 2.1.7 有哪些评估回归模型的指标？
![alt text](image-2.png)


#### 2.1.8 什么是正规方程？

#### 2.1.9 梯度下降法找到的一定是下降最快的方向吗？
不一定，它只是目标函数在当前的点的切平面上下降最快的方向。

在实际执行期中，牛顿方向（考虑海森矩阵）才一般被认为是下降最快的方向，可以达到超线性的收敛速度。梯度下降类的算法的收敛速度一般是线性甚至次线性的（在某些带复杂约束的问题）。



### 2.2 LR

也称为"对数几率回归"。

1. 分类，经典的二分类算法！
2. LR的过程：面对一个回归或者分类问题，建立代价函数，然后通过优化方法迭代求解出最优的模型参数，然后测试验证这个求解的模型的好坏。
3. **Logistic 回归虽然名字里带“回归”，但是它实际上是一种分类方法，主要用于两分类问题（即输出只有两种，分别代表两个类别）**
4. 回归模型中，y 是一个定性变量，比如 y = 0 或 1，logistic 方法主要应用于研究某些事件发生的概率。
5. **LR的本质：极大似然估计**
6. LR的激活函数：**Sigmoid**
7. LR的代价函数：交叉熵


优点：    
1. 速度快，适合二分类问题
2. 简单易于理解，直接看到各个特征的权重
3. 能容易地更新模型吸收新的数据
缺点：  
对数据和场景的适应能力有局限性，不如决策树算法适应性那么强。   

LR中最核心的概念是 Sigmoid 函数，Sigmoid函数可以看成LR的激活函数。

**Regression 常规步骤：**
1. 寻找h函数（即预测函数）
2. 构造J函数（损失函数）
3. 想办法（迭代）使得J函数最小并求得回归参数（θ）









#### 2.2.1 为什么 LR 要使用 sigmoid 函数？
1. 广义模型推导所得 
2. 满足统计的最大熵模型 
3. 性质优秀，方便使用
（Sigmoid函数是平滑的，而且任意阶可导，一阶二阶导数可以直接由函数值得到不用进行求导，这在实现中很实用）

#### 2.2.2 为什么常常要做特征组合（特征交叉）？
LR模型属于线性模型，线性模型不能很好处理非线性特征，特征组合可以引入非线性特征，提升模型的表达能力。  
另外，基本特征可以认为是全局建模，组合特征更加精细，是个性化建模，但对全局建模会对部分样本有偏，对每一个样本建模又会导致数据爆炸，过拟合，所以基本特征+特征组合兼顾了全局和个性化。    



#### 2.2.3 LR和线性回归的关系
![alt text](image-3.png)

**共同点**：
![alt text](image-4.png)




#### 2.2.4 LR参数求解的优化方法？(机器学习中常用的最优化方法)
梯度下降法，随机梯度下降法，牛顿法，拟牛顿法（LBFGS，BFGS,OWLQN）


目的都是求解某个函数的极小值。




### 2.3 Lasso

![alt text](image-5.png)

### 2.4 Ridge

![alt text](image-6.png)



### 2.5 对比
![alt text](image-7.png)








## 3.验证方式



### 3.1 什么是过拟合？产生过拟合原因?
指模型在训练集上的效果很好,在测试集上的预测效果很差.
1. 数据有噪声
2. 训练数据不足，有限的训练数据
3. 训练模型过度导致模型非常复杂

### 3.2 如何避免过拟合问题？
![alt text](image-8.png)



### 3.3 什么是机器学习的欠拟合？
模型复杂度低或者数据集太小,对模型数据的拟合程度不高,因此模型在训练集上的效果就不好.



### 3.4 如何避免欠拟合问题？
1. 增加样本的数量
2. 增加样本特征的个数
3. 可以进行特征维度扩展
4. 减少正则化参数
5. 使用集成学习方法，如Bagging


### 3.5 什么是交叉验证？交叉验证的作用是什么？
将原始dataset划分为两个部分.一部分为训练集用来训练模型,另外一部分作为测试集测试模型效果.

1. 交叉验证是用来评估模型在新的数据集上的预测效果,也可以一定程度上减小模型的过拟合
2. 还可以从有限的数据中获取尽能多的有效信息。


### 3.6 交叉验证主要有哪几种方法？
1. 留出法:简单地将原始数据集划分为训练集,验证集,测试集三个部分.
2. k折交叉验证:(一般取5折交叉验证或者10折交叉验证)
3. LOO留一法: (只留一个样本作为数据的测试集,其余作为训练集)---只适用于较少的数据集
4. Bootstrap方法:(会引入样本偏差)

### 3.7 什么是K折交叉验证？
将原始数据集划分为k个子集，将其中一个子集作为验证集，其余k-1个子集作为训练集，如此训练和验证一轮称为一次交叉验证。
交叉验证重复k次，每个子集都做一次验证集，得到k个模型，加权平均k个模型的结果作为评估整体模型的依据。


### 3.8 如何在K折交叉验证中选择K？
k越大，不一定效果越好，而且越大的k会加大训练时间；
在选择k时，需要考虑最小化数据集之间的方差，比如对于2分类任务，采用2折交叉验证，即将原始数据集对半分，若此时训练集中都是A类别，验证集中都是B类别，则交叉验证效果会非常差。

### 3.9 网格搜索（GridSearchCV）
一种调优方法，在参数列表中进行穷举搜索，对每种情况进行训练，找到最优的参数。


### 3.10 随机搜素（RandomizedSearchCV）
从超参数空间中随机采样一定数量的组合进行评估，从中选出表现最好的一组。



### 3.11 区别
网格搜索（Grid Search）和随机搜索（Random Search）都是超参数调优 的常用方法，用于在机器学习模型中寻找最优的超参数组合。虽然它们的目标相同，但在实现方式、效率、适用场景等方面有明显区别。

![alt text](image-9.png)


## 4.分类

### 4.1 几个易混淆的概念
+ 准确率（Accuracy）
+ 精准率(Precision) 
+ 召回率(Recall) 


准确率是所有判断正确的样本占所有样本的比例；   
精确率是所有判断为正例的样本中真正的正例占所有判断为正例的样本的比例；   
召回率则是所有正例中被判断出来的比率。   

### 4.2 P-R曲线

![alt text](image-11.png)


横轴为**召回率(查全率)**，纵轴为**精准率(查准率)**;  
引入“平衡点”(BEP)来度量，表示“查准率=查全率”时的取值，值越大表明分类器性能越好。




### 4.3 F1-Score
![alt text](image-12.png)
准确率和召回率的权衡: 只有在召回率Recall和精确率  

Precision都高的情况下，F1 score才会很高，比BEP更为常用。   




## 5. 正则化

### 5.1 什么是正则化？如何理解正则化？
**定义:** 在损失函数后加上一个正则化项（惩罚项），其实就是常说的结构风险最小化策略，即损失函数 加上正则化。一般模型越复杂，正则化值越大。   

正则化项是用来对模型中某些参数进行约束，正则化的一般形式：     

**第一项是损失函数（经验风险），第二项是正则化项**   

公式可以看出，加上惩罚项后损失函数的值会增大，要想损失函数最小，惩罚项的值要尽可能的小，模型参数就要尽可能的小，这样就能减小模型参数，使得模型更加简单。    


### 5.2 为何要常对数据做归一化？
1. 归一化后加快的梯度下降对最优解的速度。
2. 归一化有可能提高精度。


### 5.3 归一化和标准化的区别
标准化是依照特征矩阵的列处理数据，其通过求z-score的方法，将样本的特征值转换到同一量纲下。归一化是依照特征矩阵的行处理数据，其目的在于样本向量在点乘运算或其他核函数计算相似性时，拥有统一的标准，也就是说都转化为“单位向量”。
归一化的目的是方便比较，可以加快网络的收敛速度；标准化是将数据利用z-score（均值、方差）的方法转化为符合特定分布的数据，方便进行下一步处理，不为比较。


### 5.4 需要归一化的算法有哪些？这些模型需要归一化的主要原因？

**线性回归,逻辑回归，KNN，SVM，神经网络。** 

主要是因为特征值相差很大时，运用梯度下降，损失等高线是椭圆形，需要进行多次迭代才能达到最优点，如果进行归一化了，那么等高线就是圆形的，促使SGD往原点迭代，从而导致需要迭代次数较少。   



## 6. 决策树

### 6.1 定义
定义： 决策树就是一棵树，其中跟节点和内部节点是输入特征的判定条件，叶子结点就是最终结果。
损失函数：正则化的极大似然函数；
目标是 以损失函数为目标函数的最小化。
算法通常是一个 递归的选择最优特征，并根据该特征对训练数据进行分割，使得对各个子数据集有一个最好的分类过程。
决策树量化纯度：
判断数据集“纯”的指标有三个：Gini指数、熵、错误率


### 6.2 决策树的数据split原理或者流程？
1. 将所有样本看做一个节点
2. 根据纯度量化指标.计算每一个特征的’纯度’,根据最不’纯’的特征进行数据划分
3. 重复上述步骤,知道每一个叶子节点都足够的’纯’或者达到停止条件

背诵：按照基尼指数、信息增益来选择特征，保证划分后纯度尽可能高。



### 6.3 构造决策树的步骤？
1. 特征选择
2. 决策树的生成（包含预剪枝）  ---- 只考虑局部最优
3. 决策树的剪枝（后剪枝）      ---- 只考虑全局最优



### 6.4 决策树算法中如何避免过拟合和欠拟合？
过拟合:选择能够反映业务逻辑的训练集去产生决策树;   
剪枝操作(前置剪枝和后置剪枝); K折交叉验证(K-fold CV)
欠拟合:增加树的深度,RF



### 6.5 决策树怎么剪枝？
分为预剪枝和后剪枝，**预剪枝**是在决策树的构建过程中加入限制，比如控制叶子节点最少的样本个数，提前停止；

后剪枝是在决策树构建完成之后，根据加上正则项的结构风险最小化自下向上进行的剪枝操作.   

剪枝的目的就是**防止过拟合**，是模型在测试数据上变现良好，更加鲁棒.

### 6.6 决策树的优缺点？
决策树的优点：
1. 决策树模型可读性好，具有描述性，有助于人工分析；
2. 效率高，决策树只需要一次性构建，反复使用，每一次预测的最大计算次数不超过决策树的深度。


决策树的缺点：
1. 即使做了预剪枝，它也经常会过拟合，泛化性能很差。
2. 对中间值的缺失敏感；
3. ID3算法计算信息增益时结果偏向数值比较多的特征。


### 6.7 决策树和条件概率分布的关系？
决策树可以表示成给定条件下类的条件概率分布. 决策树中的每一条路径都对应是划分的一个条件概率分布. 每一个叶子节点都是通过多个条件之后的划分空间，在叶子节点中计算每个类的条件概率，必然会倾向于某一个类，即这个类的概率最大.




## 7. 神经网络


### **7.1 核心**
1. **核心思想与结构**
   - **特征提取机制**：通过权重矩阵将输入特征线性组合 $z = w^T x + b$
   - **非线性转换**：激活函数（如Sigmoid）生成隐藏层输出 $h = \sigma(z)$
   - **输出计算**：
     - 回归任务：$y = v^T h$（线性输出）
     - 分类任务：$y_k = \text{softmax}(v_k^T h) = \frac{e^{v_k^T h}}{\sum e^{v_m^T h}}$


2. **网络拓扑结构**
   - **输入层**：维度=特征数（如256像素→256节点）
   - **隐藏层**：通常1-3层，每层5-100个神经元
   - **输出层**：
     - 回归：1个线性神经元
     - K类分类：K个Softmax神经元



### **7.2 BP反向传播算法**


1. **算法流程**  
   | **步骤** | **操作** | **关键公式** |
   |---|---|---|
   | 1 | 初始化权重 | 随机小值（如[-0.7, 0.7]） |
   | 2 | 前向传播 | $h_k = \sigma(\sum w_{ih}x_i)$ |
   | 3 | 计算输出误差 | $e = \frac{1}{2}\sum(d_o - y_o)^2$ |
   | 4 | 误差反向传播 | $\delta_o = (d_o - y_o) \sigma'(yi_o)$ |
   | 5 | 权重更新 | $\Delta w_{ho} = \eta \delta_o h_k$ |

2. **偏导数计算**  
   - 输出层：$\delta_o = (d_o - y_o) \cdot y_o(1-y_o)$  
   - 隐藏层：$\delta_h = (\sum \delta_o w_{ho}) \cdot h_k(1-h_k)$


3. **误差反向传播（链式法则）**
   - **输出层误差**：
     $$
     \delta_o = \frac{\partial E}{\partial z_o} = 
     \begin{cases} 
     (y - \hat{y}) & \text{(回归)} \\
     (\hat{y} - y) & \text{(分类, cross-entropy)}
     \end{cases}
     $$
   - **隐藏层误差**：
     $$
     \delta_h = \frac{\partial E}{\partial z_h} = (W_{ho}^T \delta_o) \odot \sigma'(z_h)
     $$
   - **权重梯度**：
     $$
     \frac{\partial E}{\partial W_{ho}} = h^T \delta_o, \quad
     \frac{\partial E}{\partial W_{ih}} = X^T \delta_h
     $$


### **7.3 训练中的关键问题**

1. **权重初始化**  
   - 策略：小随机数（近零值）  
   - 原因：零权重导致梯度消失；大权重收敛到差解

2. **输入标准化**  
   - 方法：所有输入特征缩放至均值为0、标准差为1  
   - 作用：平衡权重更新速度，加速收敛

3. **过拟合控制技术**
   - **早停法（Early Stopping）**：在验证集误差上升时终止训练
   - **正则化**：
     - **权重衰减**：$E = \sum(y - \hat{y})^2 + \lambda \sum w_i^2$（L2正则化）  
     - **Dropout**：训练时随机屏蔽50%神经元
   - **数据增强**：旋转/平移图像样本（用于ZIP码识别）


4. **局部最小值问题**  
   | **问题类型** | **特征** | **应对策略** |
   |---|---|---|
   | 局部极小值 | 误差曲面的低谷 | 多随机初始化（5-10次） |
   | 鞍点 | 梯度为0的非极小点 | 动量优化（momentum） |

5. **梯度消失问题**
   - **原因**：Sigmoid导数最大值仅0.25，深层网络梯度连乘后趋近0
   - **解决方案**：
     - 使用ReLU激活函数（导数恒为1或0）
     - 残差连接（ResNet）
     - 梯度裁剪（限制梯度范围）



### **7.4 网络结构设计**

1. **隐藏层配置**
   | **数据复杂度** | **推荐结构** | **说明** |
   |---|---|---|
   | 简单（线性可分） | 单隐藏层，5-10神经元 | 如XOR问题 |
   | 中等（手写数字） | 1-2隐藏层，12-50神经元 | 如ZIP编码数据集 |
   | 复杂（图像分类） | 卷积神经网络+全连接 | 使用ReLU |

2. **权重初始化方法**
   - **Xavier初始化**：$W \sim \mathcal{U}(-\sqrt{\frac{6}{n_{in}+n_{out}}}, \sqrt{\frac{6}{n_{in}+n_{out}}})$
   - **He初始化**（ReLU适用）：$W \sim \mathcal{N}(0, \sqrt{\frac{2}{n_{in}}})$

3. **超参数调优**
   ```mermaid
   graph TB
   A[学习率η] --> B[网格搜索：0.001, 0.01, 0.1]
   C[正则系数λ] --> D[交叉验证选择]
   E[批量大小] --> F[32/64/128样本/批]
   ```

| **组件** | **推荐策略** | **注意事项** |
|---|---|---|
| **隐藏层数** | 1-3层 | 层数增加提升特征层次性 |
| **每层神经元数** | 5-100个 | 输入数据复杂时增加单元数 |
| **输出层** | 回归：线性单元<br>分类：Softmax | 二分类可用Sigmoid |

---


### **7.5 案例分析：ZIP编码识别**
1. **任务**：手写数字识别（0-9）  
2. **网络结构**（Net-7）  
   - 输入：16×16像素图像（256维）  
   - 隐藏层：12个神经元（Sigmoid激活）  
   - 输出层：10个神经元（Softmax）  
3. **性能**：  
   - 测试错误率：8.2%（优于线性分类器12.2%）  
   - 处理机制：非线性分离重叠数字类别

> 💡 **误差曲面特性**  
> 平坦区：$\sigma(z) \approx 0$ 或 $1$ → 梯度消失  
> 局部极小：随机初始化+多次训练避免陷入



**附：激活函数导数特性**  
Sigmoid导数：$\sigma'(z) = \sigma(z)(1-\sigma(z))$  
- 最大梯度为0.25（当$z=0$时）  
- 输入$|z| > 5$时梯度接近0 → 参数初始化需避免大权重  

**考试重点**：  
① BP算法权重更新公式推导  
② 过拟合解决方案对比（早停 vs 正则化）  
③ Sigmoid梯度消失原因分析





## 8. SVM 支持向量机

### 8.1 支持向量分类器 (Support Vector Classifier or  SVC)

#### 8.1.1 最优分类超平面
- **目标**：在两类线性可分数据中寻找间隔最大的超平面  
  $$\min \frac{1}{2} \| \mathbf{w} \|^2 \quad \text{s.t.} \quad y_i (\mathbf{w}^T \mathbf{x}_i + b) \geq 1$$
- **支持向量**：位于间隔边界上的样本点（决定超平面位置）
- **决策函数**：$f(\mathbf{x}) = \text{sgn} \left( \sum_{i} \lambda_i y_i \mathbf{x}_i^T \mathbf{x} + b \right)$



#### 8.1.2 软间隔与松弛变量
- **核心问题**：处理线性不可分数据（类间重叠）
- **松弛变量 $\xi_i$**：允许分类错误  
  $$\min \frac{1}{2} \| \mathbf{w} \|^2 + C \sum_{i=1}^N \xi_i \quad \text{s.t.} \quad y_i (\mathbf{w}^T \mathbf{x}_i + b) \geq 1 - \xi_i, \quad \xi_i \geq 0$$
- **参数 $C$**：平衡间隔最大化与分类错误惩罚  
  - $C \to \infty$：严格分类 → 可能导致过拟合  
  - $C \to 0$：容忍错误 → 模型简单但可能欠拟合



#### 8.1.3 拉格朗日对偶问题
- **原始问题 → 对偶形式**：  
  $$\max_{\lambda} \sum_{i=1}^N \lambda_i - \frac{1}{2} \sum_{i,j} \lambda_i \lambda_j y_i y_j \mathbf{x}_i^T \mathbf{x}_j$$  
  $$\text{s.t.} \quad \sum_{i} \lambda_i y_i = 0, \quad 0 \leq \lambda_i \leq C$$
- **KKT条件**：$\lambda_i [y_i (\mathbf{w}^T \mathbf{x}_i + b) - 1 + \xi_i] = 0$
- **支持向量判定**：$\lambda_i > 0$ 的样本为支持向量

---

### 8.2 支持向量机与核方法 (SVM with Kernels)

#### 8.2.1 核技巧原理
- **核心思想**：将数据映射到高维空间实现线性可分  
  $$\mathbf{x} \to \phi(\mathbf{x}) \quad \Rightarrow \quad \text{决策函数：} f(\mathbf{x}) = \text{sgn} \left( \sum \lambda_i y_i \color{red}{K(\mathbf{x}_i, \mathbf{x})} + b \right)$$
- **核函数 $K(\mathbf{x}_i, \mathbf{x}_j) = \phi(\mathbf{x}_i)^T \phi(\mathbf{x}_j)$**：避免显式计算 $\phi(\mathbf{x})$
- **常用核函数**：  
  | 核函数类型       | 公式                          | 特点                     |
  |------------------|-------------------------------|--------------------------|
  | 线性核           | $K(\mathbf{x}_i, \mathbf{x}_j) = \mathbf{x}_i^T \mathbf{x}_j$ | 无参数，适用于线性可分   |
  | 多项式核         | $(1 + \mathbf{x}_i^T \mathbf{x}_j)^d$      | $d$ 控制复杂度           |
  | 高斯核 (RBF)     | $\exp(-\gamma \| \mathbf{x}_i - \mathbf{x}_j \|^2)$ | $\gamma$ 控制样本影响范围 |

####  8.2.2 SVM的惩罚函数视角
- **等价优化问题**：  
  $$\min \sum_{i=1}^N [1 - y_i f(\mathbf{x}_i)]_+ + \frac{\lambda}{2} \| \mathbf{w} \|^2$$
  - $[z]_+ = \max(0, z)$：合页损失（Hinge Loss）
  - 本质：L2正则化 + 分类边界惩罚

#### 8.2.3 维度灾难与泛化能力
- **优势**：通过核函数在高维隐空间操作 → 避免维度灾难
- **实验结论**：SVM在高维数据中比KNN更抗过拟合（见图：Test Error Curves）

---

### 8.3 支持向量回归 (SVM for Regression)
#### 8.3.1 $\epsilon$-不敏感损失函数
- **核心思想**：构造宽度为 $2\epsilon$ 的间隔带包容数据  
  $$\min \frac{1}{2} \| \mathbf{w} \|^2 + C \sum_{i=1}^N (\xi_i + \xi_i^*)$$  
  $$\text{s.t.} \quad \begin{cases} 
  y_i - (\mathbf{w}^T \phi(\mathbf{x}_i) + b) \leq \epsilon + \xi_i \\
  (\mathbf{w}^T \phi(\mathbf{x}_i) + b) - y_i \leq \epsilon + \xi_i^* \\
  \xi_i, \xi_i^* \geq 0 
  \end{cases}$$
- **参数**：  
  - $\epsilon$：控制回归带宽度（大 $\epsilon$ → 模型简单）  
  - $C$：平衡平坦性与误差容忍度

#### 8.3.2 对偶问题
- **回归形式**：$f(\mathbf{x}) = \sum_{i} (\lambda_i - \lambda_i^*) K(\mathbf{x}_i, \mathbf{x}) + b$
- **支持向量**：$|\lambda_i - \lambda_i^*| > 0$ 的样本（位于间隔带外）

---

### **IV. 关键对比与考试重点**
| **概念**          | 分类SVM                         | 回归SVM                     |
|--------------------|--------------------------------|----------------------------|
| **目标**          | 最大化分类间隔                | 最小化 $\epsilon$-带外误差 |
| **损失函数**      | 合页损失 (Hinge Loss)         | $\epsilon$-不敏感损失      |
| **支持向量**      | 边界上的点 & 错分点           | 落在间隔带外的点           |
| **参数影响**      | $C$ 控制分类严格性            | $\epsilon$ 控制回归带宽度  |

> **重要概念**：  
> 1. 必考推导：软间隔SVM对偶问题、KKT条件  
> 2. 核函数选择：高斯核参数 $\gamma$ 的作用（$\gamma \uparrow$ → 模型更复杂）  
> 3. 回归SVM图解：理解 $\xi_i$ 和 $\xi_i^*$ 对应上/下界误差




- 第四章介绍了当两个类别线性可分时的最优分离超平面
- 本章讨论对不可分情况（类别重叠）的扩展
- 支持向量机(SVM)通过在转换后的特征空间构建线性边界来产生非线性边界
- 本章还介绍了Fisher线性判别分析(LDA)的泛化方法：
  - 灵活判别分析：以类似SVM的方式构建非线性边界
  - 惩罚判别分析：用于特征高度相关的信号和图像分类问题
  - 混合判别分析：用于处理形状不规则的类别


## 9. 聚类分析

### 9.1 介绍

1. 聚类的本质:
- 将对象分组,使同组内对象相似,不同组间对象不同
- 组内距离(intra-cluster distances)最小化
- 组间距离(inter-cluster distances)最大化

2. 聚类的应用:
- 理解(Understanding):分组相关文档、基因蛋白、股票等
- 总结(Summarization):减少大数据集的规模

3. **聚类的类型**:
+ 基于划分（Partition-based）：K-means
+ 层次聚类（Hierarchical Clustering）：
  + 凝聚层次聚类（AGNES, Bottom-up）：从最细粒度（每个点自成一簇）开始，逐步合并相似的簇。
  + 分裂层次聚类（DIANA, Top-down）：从整体数据（所有点一个簇）开始，逐步拆分不相似的子簇。
+ 基于密度（Density-based）：DBSCAN
+ 模型基于（Model-based / Mixture Models）：高斯混合模型（Gaussian Mixture Model, GMM）



**重要问题：如何求距离？**
  1. Euclidean Distance（l2 norm）
   表达式为 $\sqrt{\sum_{i=1}^{n}(x_{i}-y_{i})^2}$
  2. Manhattan Distance（l1 norm）
   表达式为 $\sum_{i=1}^{n}|x_{i}-y_{i}|$
  3. Minkowski Distance（L-p norm）
   表达式为 $\sum_{i=1}^{n}|x_{i}-y_{i}|^{p}$
  4. chebyshev Distance（ l-infinity norm）
    表达式为 $\max_{i=1}^{n}|x_{i}-y_{i}|$
   


### 9.2 基于划分（Partition-based）

**代表方法**：
+ K-means
+ 变体k-means++、bi-kmeans、kernel k-means

**主要特点**：
+ 需要事先指定聚类数 $K$。
+ 通过迭代式地进行“分配样本到簇”与“更新簇中心点”或“更新样本原型”的过程来收敛。
+ 对球状或凸形聚类效果较好，但对于非球状或大小差异较大的簇，效果缺陷明显。
+ 适合大规模数据，计算开销相对较低，但**对初值和超参数（如K）较敏感**。
+ 对异常数据比较敏感。



#### 9.2.1  K-means
**需要的预设：k和初始中心点**

一般来说，初始中心点是随机生成的，且初始中心点的选取对聚类结果影响很大。

+ 聚类数目（K）的选择：
  1. **elbow方法** ：Elbow方法是基于聚类内部的“紧致度”衡量指标（如簇内平方误差和 $\text{SSE} = \sum_{k=1}^{K} \sum_{\mathbf{x} \in C_k} \|\mathbf{x} - \mathbf{\mu}_k \|^2$）来评估聚类效果；通常，该指标随着聚类数 $K$ 的增大而减小，但当 $K$ 超过某个合理值时，指标的下降幅度会突然变得缓慢，形成一处明显的“折点”，这就是该方法名称中“肘部（elbow）”的由来。
  2. **silhouette方法（轮廓系数法）** ：
  综合考虑了簇内相似度（凝聚性）和簇间相似度（可分离性）。对于每个样本 $\mathbf{x}_i$，它的轮廓系数 $s(\mathbf{x}_i)$ 定义为
  $$
    s(\mathbf{x}_i) = \frac{b(\mathbf{x}_i) - a(\mathbf{x}_i)}{\max\{a(\mathbf{x}_i),\; b(\mathbf{x}_i)\}}
  $$  
  + $s(\mathbf{x}_i)$ 的取值在 $[-1, 1]$ 之间：值越接近1，表明该样本与所在簇的距离远小于与其他簇的距离（聚类效果好）。值越接近-1，表明该样本被“分错”簇的可能性很大。
  > $a(\mathbf{x}_i)$ 表示该样本与其所在簇中其他样本的平均距离（簇内平均距离）。
  > $b(\mathbf{x}_i)$ 表示该样本与相邻簇（距离最近的其他簇）中样本的平均距离。
  3. **Gap Statistic**
  4. **Dunn Index**



#### 9.2.2  K-means++
k-means++是针对k-means中初始质心点选取的优化算法。

流程如下：
1. 随机选取一个数据点作为初始的聚类中心
2. 当聚类中心数量小于k时：计算每个数据点与当前已有聚类中心的最短距离，用 D(x)表示，这个值越大，表示被选取为下一个聚类中心的概率越大，最后使用轮盘法选取下一个聚类中心


#### 9.2.3  bi-Kmeans
bi-kmeans是针对kmeans算法会陷入局部最优的缺陷进行的改进算法。

流程如下：
1. 将所有点视为一个簇
2. 当簇的个数小于K时对每一个簇计算总误差，在给定的簇上面进行 k-means 聚类（k=2）计算将该簇一分为二之后的总误差
3. 选取使得误差最小的那个簇进行划分操作



### 9.3 基于密度（Density-based）
k-means算法对于凸性数据具有良好的效果，能够根据距离来讲数据分为球状类的簇，但对于非凸形状的数据点，这个时候就需要用到基于密度的聚类方法了

代表方法：
+ DBSCAN
+ OPTICS

**主要特点**：
+ 需要提前确定ε和M的值  
+ 不需要提前设置聚类的个数
+ 对初值选取敏感，对噪声不敏感
+ 对密度不均的数据聚合效果（DBSCAN不好，OPTICS较好）

#### 9.3.1 DBSCAN

流程如下：
1. 标记所有对象为unvisited  
2. 当有标记对象时  
    1. 随机选取一个unvisited对象 \( p \)  
    2. 标记 \( p \) 为visited  
    3. 如果 \( p \) 的 \( \varepsilon \) 邻域内至少有 \( M \) 个对象，则  
        1. 创建一个新的簇 \( C \)，并把 \( p \) 放入 \( C \) 中  
        2. 设 \( N \) 是 \( p \) 的 \( \varepsilon \) 邻域内的集合，对 \( N \) 中的每个点 \( p' \)  
            1. 如果点 \( p' \) 是unvisited  
                1. 标记 \( p' \) 为visited  
                2. 如果 \( p' \) 的 \( \varepsilon \) 邻域至少有 \( M \) 个对象，则把这些点添加到 \( N \)  
                3. 如果 \( p' \) 还不是任何簇的成员，则把 \( p' \) 添加到 \( C \)  
        3. 保存 \( C \)  
    4. 否则标记 \( p \) 为噪声 



**DBSCAN算法关键概念:**   
- ε-邻域:对象半径ε内的区域
- 核心点:ε-邻域内至少包含MinPts个对象的点
- 直接密度可达:从核心点出发能直接到达的点
- 密度可达:通过多个核心点间接到达的点
- 密度相连:两点可从同一点密度可达




#### 9.3.2 OPTICS
在DBSCAN算法中，使用了统一的值，当数据密度不均匀的时候，如果设置了较小的值，则较稀疏的cluster中的节点密度会小于
，会被认为是边界点而不被用于进一步的扩展；如果设置了较大的
值，则密度较大且离的比较近的cluster容易被划分为同一个cluster。


对于密度不均的数据选取一个合适的是很困难的，对于高维数据，由于维度灾难(Curse of dimensionality),ε的选取将变得更加困难。

### 9.4 层次聚类（Hierarchical Clustering）
前面介绍的几种算法确实可以在较小的复杂度内获取较好的结果，但是这几种算法却存在一个链式效应的现象，比如：A与B相似，B与C相似，那么在聚类的时候便会将A、B、C聚合到一起，但是如果A与C不相似，就会造成聚类误差，严重的时候这个误差可以一直传递下去。为了降低链式效应，这时候层次聚类就该发挥作用了。




**簇间相似度度量：**  
除了需要衡量对象之间的距离之外，有些聚类算法（如层次聚类）还需要衡量cluster之间的距离 
+ **single  linkage**：也叫最短距离法，定义两个簇之间的距离为两个簇中距离最近的两个样本点的距离。比如有簇 A 和簇 B，在 A 中找一个点，B 中找一个点，使这两个点距离最短，该距离就是两簇距离。优点是能识别细长形状的簇结构；缺点是易受噪声和离群点影响，可能形成链状聚类结果 。
+ **complete  linkage**：又称最长距离法，将两个簇之间的距离定义为两个簇中距离最远的两个样本点的距离。即找出簇 A 和簇 B 中距离最远的一对点，其距离为两簇距离。能产生紧凑的聚类结果，对噪声和离群点相对不敏感，但可能会合并距离较远的簇 。
+ **average  linkage**：计算两个簇中所有样本点对之间距离的平均值，以此作为簇间距离。综合考虑了簇内多个样本点的关系，聚类结果相对稳健，能避免单链接和全链接的极端情况 。
+ **ward  linkage**：基于方差分析思想，目标是最小化合并簇时增加的簇内离差平方和。每次选择合并使簇内总方差增加最小的两个簇。倾向于产生大小相似的簇，在数据分布较为均匀时效果较好 。


#### 9.4.1 凝聚层次聚类（AGNES, Bottom-up）
称自底向上（bottom-up）的层次聚类，每一个对象最开始都是一个 cluster，每次按一定的准则将最相近的两个 cluster 合并生成一个新的 cluster，如此往复，直至最终所有的对象都属于一个 cluster。这里主要关注此类算法。




过程如下：
1. 初始时每个样本为一个 cluster，计算距离矩阵 D，其中元素$D_{ij}$为样本点$D_{i}$和$D_{j}$之间的距离；
2. 遍历距离矩阵 D，找出其中的最小距离（对角线上的除外），并由此得到拥有最小距离的两个 cluster 的编号，将这两个 cluster 合并为一个新的 cluster 并依据 cluster 距离度量方法更新距离矩阵 D（删除这两个 cluster 对应的行和列，并把由新 cluster 所算出来的距离向量插入 D 中），存储本次合并的相关信息；
3. 重复 2 的过程，直至最终只剩下一个 cluster 。 






#### 9.4.2 分割层次聚类（SINGLE, Complete, Average）
又称自顶向下（top-down）的层次聚类，最开始所有的对象均属于一个 cluster，每次按一定的准则将某个 cluster 划分为多个 cluster，如此往复，直至每个对象均是一个 cluster。
   




### 9.5 比较总结

|算法类型|适合的数据类型|抗噪点性能|聚类形状|算法效率|
| ---- | ---- | ---- | ---- | ---- |
|kmeans|混合型|较差|球形|很高|
|k-means++|混合型|一般|球形|较高|
|bi-kmeans|混合型|一般|球形|较高|
|DBSCAN|数值型|较好|任意形状|一般|
|OPTICS|数值型|较好|任意形状|一般|
|Agglomerative|混合型|较好|任意形状|较差| 













## 10. 集成学习

### **10.1 什么是学习器？**  
广义指代所有通过数据训练得到的预测模型

| 名称          | 定义                                               | 示例                     |
   |---------------|----------------------------------------------------------------------|--------------------------|
   | **学习器**    | 广义指代所有通过数据训练得到的预测模型                                | SVM、决策树、神经网络     |
   | **基学习器**  | 同质集成中的个体学习器                     | Bagging中的决策树        
   | **弱学习器**  | 性能略优于随机猜测的简单模型（错误率 < 50%）                         | AdaBoost中的决策树桩      |
   | **强学习器**  | 高精度模型，或由弱学习器组合而成的集成模型                           | 深度神经网络、XGBoost    |


**学习器的性能受限于：**
+ **假设空间局限性**（如线性模型无法拟合非线性数据）。  
+ **噪声干扰与过拟合风险**。  
+ **单一模型的表达瓶颈**。  

**解决方案：**  
- **集成学习**：组合多个学习器（如Boosting/Bagging），提升泛化能力。  
- **核方法**：通过非线性映射扩展学习器的表达能力（如KSVM、KPCA）。  

### **10.2 Boosting和Bagging**
集成学习可以分为两种：`Boosting`和`Bagging`。

| **特征**          | **Bagging**                            | **Boosting**                          |
|--------------------|----------------------------------------|----------------------------------------|
| **核心理念**       | **并行**生成多个独立模型，降低方差      | **串行**生成依赖模型，逐步修正错误，降低偏差 |
| **训练顺序**       | 基学习器独立训练，**可并行化**          | 弱学习器顺序训练，**必须串行**          |
| **数据使用**       | 自助采样（Bootstrap）<br>每个基学习器用**不同子集** | 每轮用**全部数据**，但调整样本权重        |
| **样本权重**       | 所有样本**权重相同**（均匀采样）         | 错误样本**权重增加**（聚焦难例）         |
| **基学习器关系**   | **相互独立**，无依赖关系                | **强依赖**，后序模型修正前序错误         |
| **结合策略**       | 分类：投票法<br>回归：平均法              | 加权投票（准确率高的模型权重更大）       |
| **目标效果**       | **降低方差**<br>适合高方差模型（如深度决策树） | **降低偏差**<br>适合高偏差模型（如树桩）  |
| **过拟合风险**     | 不易过拟合（平均抑制噪声）               | 易过拟合（需控制迭代次数/学习率）        |
| **异常值敏感度**   | 不敏感                                 | 敏感（错误样本权重持续增加）             |
| **代表性算法**     | 随机森林（Random Forest）              | AdaBoost, Gradient Boosting, XGBoost   |
| **计算效率**       | 高效（可并行）                         | 较低（串行依赖）                       |
| **噪声鲁棒性**    | 高（平均抑制异常值）             | 低（异常值权重被放大）           |
| **结果稳定性**    | 高（多次运行结果一致）           | 中（依赖初始样本权重）           |
| **超参数调优**    | 简单（通常默认设置即可）         | 复杂（需调迭代次数/学习率/正则化）|




####  **10.2.1 数据采样机制**
- **Bagging**  
  - 使用 **Bootstrap 抽样**：从原始数据集有放回抽取样本（每个基学习器训练集大小 ≈ 原始集，但包含重复样本）。  
  - **包外估计 (OOB)**：未抽中的样本（约 37%）用于验证模型泛化能力。  
- **Boosting**  
  - **全数据集 + 动态权重**：每轮迭代调整样本权重，增加分类错误样本的权重。  
  - **核心思想**：后续模型专注修正前序模型的错误（如 AdaBoost 的加权重训练）。 



####  **10.2.2 偏差-方差权衡**
- **Bagging主要降低方差**  
  - 场景：适用于**复杂模型**（如过拟合的决策树），通过平均预测平滑噪声。  
  - 示例：随机森林中，若非剪枝树单个错误率 40%，集成 100 棵树后错误率可降至 10% 以下。  
- **Boosting主要降低偏差**  
  - 场景：适用于**弱模型**（如深度=1 的决策树桩），逐步优化训练集拟合。  
  - 风险：过度迭代会导致过拟合（见下图迭代次数与错误率关系）。  




#### **10.2.3 怎么选**
- **选 Bagging 当**：  
  - 基学习器是**高方差模型**（如深度决策树、神经网络）。  
  - 需要**快速并行训练**（如大数据场景）。  
  - 数据**含较多噪声**。  

- **选 Boosting 当**：  
  - 基学习器是**简单模型**（如浅层树）。  
  - 追求**高精度**且可接受较长训练时间。  
  - 数据**相对干净**，需捕捉复杂模式。  

> 二者可结合：如 **随机森林 + Gradient Boosting**（XGBoost/LightGBM）在竞赛中表现优异。


---

### **10.3 Boosting方法**

#### **10.3.1 核心**
1. **核心思想**  
   - 结合多个弱分类器（错误率略优于随机猜测）构建强分类器。  
   - **核心目标**：通过加权组合弱分类器提升整体性能。  

2. **集成学习基础**  
   - **个体与集成关系**：  
     - 集成学习通过结合多个学习器提升性能，要求个体学习器“好而不同”（高准确性和多样性）。  
   - **误差分析**：  
     - 假设基分类器错误率相互独立时，集成错误率随分类器数量增加**指数级下降**（Hoeffding不等式）。  
     - 实际中基学习器存在相关性，需平衡准确性与多样性。  



#### **10.3.2 拟合与加法模型**  
1. **加法模型结构**  
   - Boosting本质为拟合**加法模型**：  
     $$  
     f(x) = \sum_{m=1}^M \beta_m b(x; \gamma_m)
     $$  
     - $b(x; \gamma_m)$ 为基学习器（如决策树桩），$\beta_m$ 为权重系数。  
   - **训练策略**：前向分步算法（Forward Stagewise Additive Modeling），逐轮添加弱学习器优化目标函数。  

2. **前向分步算法流程**  
   - 初始化：设初始模型 $f_0(x) = 0$。  
   - 迭代 $m=1$ 至 $M$：  
     1. 优化当前轮次：求解 $\beta_m$ 和 $\gamma_m$ 最小化损失函数（如平方损失、指数损失）。  
     2. 更新模型：$f_m(x) = f_{m-1}(x) + \beta_m b(x; \gamma_m)$。  

---

#### **10.3.3 AdaBoost**      
1. **AdaBoost算法流程**      
   - **输入**：训练集 $D = \{(x_i, y_i)\}_{i=1}^N$（$y_i \in \{-1, 1\}$），基学习器（如树桩）。  
   - **初始化权重**: $w_i = \frac{1}{N}$.  
   - **迭代 $m=1$ 至 $M$**：  
     1. 训练基分类器 $G_m(x)$ 最小化加权错误率 $\epsilon_m = \sum_{i=1}^N w_i I(y_i \neq G_m(x_i))$.  
     2. 计算分类器权重：$\alpha_m = \frac{1}{2} \ln \left( \frac{1-\epsilon_m}{\epsilon_m} \right)$.  
     3. **更新样本权重**：  
        $$
        w_i \leftarrow w_i \cdot \exp \left[ -\alpha_m y_i G_m(x_i) \right], \quad \text{后归一化}.
        $$  
     4. 更新模型：$f(x) = \sum_{m=1}^M \alpha_m G_m(x)$.  
   - **输出**：$G(x) = \text{sign}[f(x)]$.  

2. **指数损失函数**  
   - 损失函数：$L(y, f(x)) = \exp[-y f(x)]$.  
   - **性质**：AdaBoost等价于最小化指数损失的前向加法模型。  
   - **示例效果**：  
     - 单树桩测试错误率→45.8%；400轮Boosting后→5.8%。  

3. **权重机制**  
   - **样本权重**：错误样本权重增加，正确样本权重减少（聚焦难分类样本）。  
   - **分类器权重**：准确率高的分类器权重更大（$\alpha_m$ 与 $\epsilon_m$ 负相关）。  

---

#### **10.3.4 Boosting Trees**  
1. **模型形式**  
   - 基学习器为决策树：  
     $$
     f(x) = \sum_{m=1}^M \beta_m T(x; \Theta_m)
     $$  
     - $T(x; \Theta_m)$ 为决策树，$\Theta_m$ 为树参数。  


2. **训练策略**  
   - 递归拟合残差：  
     1. 计算当前模型的残差 $r_{i} = y_i - f_{m-1}(x_i)$.  
     2. 以残差为目标训练新树 $T_m$.  
     3. 更新模型：$f_m(x) = f_{m-1}(x) + T_m(x)$.  


---

#### **10.3.5 Gradient Boosting Trees** 
Gradient Boosting（梯度提升）是一种集成弱学习模型的机器学习方法，例如GBDT就是集成了多个弱决策树模型。


1. **梯度提升框架**  
   - **核心思想**：将优化问题转化为梯度下降。  
   - **步骤**：  
     1. 初始化模型 $f_0(x) = \arg\min_\gamma \sum_{i=1}^N L(y_i, \gamma)$.  
     2. 迭代 $m=1$ 至 $M$：  
        - 计算伪残差：$r_{im} = -\left[ \frac{\partial L(y_i, f(x_i))}{\partial f(x_i)} \right]_{f(x)=f_{m-1}(x)}$.  
        - 拟合基学习器 $T_m(x)$ 预测伪残差。  
        - 更新模型：$f_m(x) = f_{m-1}(x) + \nu \cdot T_m(x)$（$\nu$ 为学习率）。  

2. **适用性优点**  
   - 支持任意可微损失函数（如平方损失、绝对损失）。  
   - 学习率 $\nu$ 控制过拟合风险（如 $\nu=0.1$）。  


---


### **10.4 Bagging方法**
Bagging 是Bootstrap Aggregating 的缩写，其算法的基本思想是从原始的数据集中抽取数据，形成K个随机的新训练集，然后训练出K个不同的模型。       

#### **10.4.1 核心**

**目标**：降低模型方差（Variance），提升泛化能力  
**方法**：通过 **Bootstrap 抽样**生成多份训练集，并行训练多个基学习器，通过**投票（分类）** 或 **平均（回归）** 结合预测结果。

> 核心公式：  
> $$
> \hat{f}_{\text{bag}}(x) = \frac{1}{B} \sum_{b=1}^{B} \hat{f}^{*b}(x)
> $$  
> - $B$：基学习器数量  
> - $\hat{f}^{*b}$：第 $b$ 个Bootstrap样本训练的基学习器


#### **10.4.2 Bagging流程**

##### **Bootstrap自助取样**
- 从原始训练集 $D$（大小 $N$）中**有放回随机抽取** $N$ 个样本  
- 生成 $B$ 个新数据集 $D^{*1}, D^{*2}, \dots, D^{*B}$  
- **特性**：  
    - 每个 $D^{*b}$ **包含约 63.2% 的原始数据**（其余为重复样本）  
  - **未抽中的样本（Out-of-Bag, OOB）**：占比约 36.8%，天然形成验证集（用于评估泛化能力）

##### **并行训练基学习器**
- 每个数据集 $D^{*b}$ 独立训练一个基学习器 $\hat{f}^{*b}$（如决策树、SVM等）  
- **关键要求**：基学习器应为 **高方差模型**（如未剪枝决策树），Bagging 通过平均降低其方差

##### **集成预测**
- **分类任务**：多数投票  
  $$
  \text{Class}(x) = \arg\max_{c} \sum_{b=1}^{B} I \left( \hat{f}^{*b}(x) = c \right)
  $$  
- **回归任务**：简单平均  
  $$
  \hat{f}_{\text{bag}}(x) = \frac{1}{B} \sum_{b=1}^{B} \hat{f}^{*b}(x)
  $$




#### 10.4.3 **数学本质：方差削减原理**
设单个基学习器误差方差为 $\sigma^2$，各基学习器误差相关系数为 $\rho$，则 Bagging 集成的方差为： 

$$
\text{Var}(\hat{f}_{\text{bag}}) = \rho \sigma^2 + \frac{1-\rho}{B} \sigma^2
$$  

- 当基学习器**完全独立**（$\rho = 0$）时：方差降至 $\frac{\sigma^2}{B}$  
- 实际中 $\rho > 0$（学习器相关），但方差仍显著低于单个模型。

> **示例**：  
> 若单棵决策树测试误差率 40%（$\sigma^2 = 0.4$），取 $B = 100$，$\rho = 0.2$：  
> $$
> \text{Var} \approx 0.2 \times 0.4 + \frac{0.8}{100} \times 0.4 = 0.0832 \quad (\text{误差率} \approx 28.8\%)
> $$




#### 10.4.4 Random Forest随机森林

Bagging 的扩展变体，引入**双重随机性**进一步降方差：  
1. **样本随机**：Bootstrap 采样  
2. **特征随机**：每棵树分裂时随机选子集特征（通常 $m = \sqrt{p}$，$p$ 为总特征数）  
- **优势**：  
  - 比标准Bagging方差更低（特征随机降低学习器间相关性 $\rho$）  
  - 处理高维数据更有效  




**多数情况下的Bagging，都是基于决策树的，构造随机森林的第一个步骤其实就是对多棵决策树进行Bagging，我们把它称为树的聚合(Bagging of Tree )。**



## 11. 核方法

### **11.1 空间与维度**  

1. **升维与降维的目的**  
   - **升维**：将低维线性不可分问题转化为高维线性可分问题（如通过多项式变换分离非线性数据）。  
   - **降维**：减少特征维度以降低计算复杂度、消除冗余信息（如PCA保留主要特征方向）。  
   - **核心原则**：升维解决可分性，降维解决效率与噪声。  

2. **示例：一维不可分问题**  
   - 一维空间中，线性函数无法分离交错的类别（如黑白点混杂）。  
   - **解决方案**：引入二次判别函数（如 $g(x) = (x-a)(x-b)$）：  
     - $g(x) \geq 0$ → 类别 $C_1$；  
     - $g(x) < 0$ → 类别 $C_2$。  
   - **本质**：通过非线性映射将问题转换到高维空间实现线性可分。  

---

### **11.2 核函数**  

#### **11.2.1 核函数定义**  
   - 核函数 $K(\mathbf{x}_i, \mathbf{x}_j) = \langle \phi(\mathbf{x}_i), \phi(\mathbf{x}_j) \rangle$ 直接计算高维特征空间的内积，**避免显式构造映射** $\phi$。  
   - **存在条件**：Mercer定理要求核矩阵半正定。  

#### **11.2.2 常用核类型**  
   - **高斯RBF核**：$K(\mathbf{x}, \mathbf{y}) = \exp\left(-\frac{\|\mathbf{x}-\mathbf{y}\|^2}{c}\right)$  
     - 参数 $c$ 控制带宽（$c \uparrow$ → 平滑度 $\uparrow$）。  
   - **多项式核**：$K(\mathbf{x}, \mathbf{y}) = (\theta + \mathbf{x}^T\mathbf{y})^d$  
     - $d$ 为多项式阶数，控制复杂度。  
   - **Sigmoidal核**：$K(\mathbf{x}, \mathbf{y}) = \tanh(\alpha \mathbf{x}^T\mathbf{y} + \theta)$  
     - 模拟神经网络激活函数。  
   - **逆多元二次核**：$K(\mathbf{x}, \mathbf{y}) = \frac{1}{\|\mathbf{x}-\mathbf{y}\|^2 + c}$  

#### **11.2.3 核函数的性质**  
   - 对称性：$K(\mathbf{x}, \mathbf{y}) = K(\mathbf{y}, \mathbf{x})$。  
   - 正定性：核矩阵 $K_{ij} = K(\mathbf{x}_i, \mathbf{x}_j)$ 半正定。  
   - **反映数据相似性**：值越大表明样本在高维空间越接近。  

---

### **11.3 核K-均值方法**  
1. **标准K-均值流程**  
   - **Step 1**：随机初始化 $K$ 个聚类中心。  
   - **Step 2**：分配样本到最近中心（欧氏距离）。  
   - **Step 3**：重新计算聚类中心（均值）。  
   - **Step 4**：重复直至中心收敛。  

2. **核化改进**  
   - **核心思想**：用核函数替代内积，隐式映射到高维空间进行聚类。  
   - **距离计算**：  
     $$
     \|\phi(\mathbf{x}) - \phi(\mathbf{c}_k)\|^2 = K(\mathbf{x}, \mathbf{x}) - 2K(\mathbf{x}, \mathbf{c}_k) + K(\mathbf{c}_k, \mathbf{c}_k)
     $$  
   - **优势**：可分离低维空间中非线性可分的簇（如同心圆数据）。  


---

### **11.4 核支持向量机（KSVM）**  
1. **非线性SVM的核化**  
   - **原始目标函数**：  
     $$
     \max_{\alpha} \sum_{i=1}^n \alpha_i - \frac{1}{2} \sum_{i,j} \alpha_i \alpha_j y_i y_j (\mathbf{x}_i^T \mathbf{x}_j)
     $$  
   - **核化形式**：  
     $$
     \max_{\alpha} \sum_{i=1}^n \alpha_i - \frac{1}{2} \sum_{i,j} \alpha_i \alpha_j y_i y_j K(\mathbf{x}_i, \mathbf{x}_j)
     $$  

2. **权向量与分类决策**  
   - 权向量：$\mathbf{w} = \sum_{i} \alpha_i y_i \phi(\mathbf{x}_i)$  
   - 决策函数：  
     $$
     f(\mathbf{x}) = \text{sign}\left(\sum_{i} \alpha_i y_i K(\mathbf{x}_i, \mathbf{x}) + b\right)
     $$  

3. **示例（二维不可分数据）**  
   - 数据集：  
     - $A = \{(1,1), (1,4), (4,1), (4,4)\}$（类1）  
     - $B = \{(2,2), (2,3), (3,2), (3,3)\}$（类2）  
   - **核函数选择**：多项式核 $K(\mathbf{x}, \mathbf{y}) = (1 + \mathbf{x}^T\mathbf{y})^2$ → 实现非线性分离。  

---

### **11.5 核主成分分析（KPCA）**  
![alt text](image-17.png)
1. **PCA核心思想**  
   - 将数据投影到方差最大的正交方向（主成分）。  
   - **协方差矩阵**：$\Sigma = \frac{1}{M} \sum \mathbf{x}_i \mathbf{x}_i^T$。  
   - **特征方程**：$\Sigma \mathbf{v} = \lambda \mathbf{v}$ → $\mathbf{v}$ 为特征向量（投影方向）。  

2. **KPCA的核化步骤**  
   - **高维映射**：$\mathbf{x} \rightarrow \phi(\mathbf{x})$，要求 $\sum \phi(\mathbf{x}_i) = 0$（中心化）。  
   - **核矩阵**：$K_{ij} = K(\mathbf{x}_i, \mathbf{x}_j)$。  
   - **特征方程**：  
     $$
     M \lambda \boldsymbol{\alpha} = \mathbf{K} \boldsymbol{\alpha}
     $$  
     - 解 $\boldsymbol{\alpha}$ 得到主成分方向。  
   - **投影坐标**：第 $k$ 个主成分上样本 $\mathbf{x}$ 的投影：  
     $$
     y_k = \sum_{i=1}^M \alpha_i^{(k)} K(\mathbf{x}_i, \mathbf{x})
     $$  

3. **KPCA vs PCA**  
   | **特性**       | **PCA**         | **KPCA**               |  
   |----------------|-----------------|------------------------|  
   | **空间**       | 原始空间        | 核映射的高维特征空间   |  
   | **可分离性**   | 仅线性可分      | 非线性可分             |  
   | **计算复杂度** | $O(d^3)$      | $O(M^3)$（样本驱动） |  





## 12. RNN循环神经网络
循环神经网络（Recurrent Neural Network，RNN）是一种具有循环连接的神经网络结构，被广泛应用于自然语言处理、语音识别、时序数据分析等任务中。相较于传统神经网络，RNN的主要特点在于它可以处理序列数据，能够捕捉到序列中的时序信息。

RNN的基本单元是一个循环单元（Recurrent Unit），它接收一个输入和一个来自上一个时间步的隐藏状态，并输出当前时间步的隐藏状态。在传统的RNN中，循环单元通常使用tanh或ReLU等激活函数。

---

### **12.1 序列建模问题与动机**
1. **槽填充任务 (Slot Filling)**  
   - **目标**：从句子中抽取结构化信息（如票务系统中的目的地/时间）  
     - 示例输入："leave Taipei on November 2nd" → 输出：`离开地=Taipei, 时间=November 2nd`
   - **核心挑战**：  
     - 相同单词（如"Taipei"）在不同上下文含义不同：  
       `arrive Taipei` → 目的地 vs `leave Taipei` → 出发地  
   - **前馈网络缺陷**：  
     - 无记忆能力，无法捕捉序列依赖（输出仅依赖当前输入）  
     - 使用 **one-hot 编码**（词向量维度=词典大小）丢失上下文信息  

---

### **12.2 RNN 基本结构与原理**
1. **核心创新：记忆单元 (Memory)**  
   ```mermaid
   graph LR
     A[输入 x_t] --> B[隐藏层 a_t]
     B --> C[输出 y_t]
     B --> D[记忆单元]
     D -->|t+1时刻| B
   ```
   - **数学表达**：  
     - $a_t = f(W_{aa}a_{t-1} + W_{ax}x_t + b_a)$ （隐藏状态）  
     - $y_t = g(W_{ya}a_t + b_y)$ （输出）  
   - **关键特性**：  
     - 记忆单元存储上一步隐藏状态 $a_{t-1}$  
     - 相同网络结构在不同时间步复用  

2. **计算示例**  
   - 参数：所有权重=1，无偏置，线性激活  
   - 输入序列：$[1,1] → [1,1] → [2,2]$  
   - 输出演化：  
     | 时间步 | 记忆输入 | 当前输入 | 新记忆(a_t) | 输出(y_t) |  
     |--------|----------|----------|-------------|-----------|  
     | t=1    | [0,0]    | [1,1]    | [1,1]       | [1,1]     |  
     | t=2    | [1,1]    | [1,1]    | [1+1+1, 1+1+1]=[3,3] | [3,3] |  
     | t=3    | [3,3]    | [2,2]    | [3+3+2, 3+3+2]=[8,8] | [8,8] |  

---

### **12.3 RNN 变体与扩展**


#### **12.3.1 网络架构改进**
| **类型**          | **记忆来源**         |  **特点**                  |
|-------------------|---------------------|----------------------------------------|
| **Elman Network** | 上一步隐藏层 $a_{t-1}$ |标准RNN实现             |
| **Jordan Network**| 上一步输出 $y_{t-1}$ | 减少梯度传播路径        |


#### **12.3.2 双向RNN (Bi-RNN)**
   - **结构**：  
     ```mermaid
     graph LR
       subgraph 正向
         x1 --> a1 --> y1
         a1 --> a2
         x2 --> a2 --> y2
       end
       subgraph 反向
         x1 --> a1' --> y1
         a1' --> a2'
         x2 --> a2' --> y2
       end
       y1 & y1' --> o1[最终输出t1]
       y2 & y2' --> o2[最终输出t2]
     ```
   - **优势**：同时利用过去和未来上下文信息（如语句时序理解）  

---

### **12.4 长短期记忆网络 (LSTM)**
![alt text](image-20.png)

#### **12.4.1 解决RNN核心问题**
   - **长期依赖失效**：普通RNN梯度消失导致无法记忆长序列  
   - **门控机制**：通过三扇门控制信息流  

#### **12.4.2 LSTM单元结构**
   ```mermaid
   graph TB
     x_t & a_t-1 --> ForgetGate
     x_t & a_t-1 --> InputGate
     x_t & a_t-1 --> OutputGate
     x_t & a_t-1 --> NewCandidate
     ForgetGate -->|f_t| CellState-1
     InputGate -->|i_t| NewCandidate
     NewCandidate -->|C_tilde_t| CellStateUpdate
     CellState-1 --> CellStateUpdate
     CellStateUpdate --> CellState_t
     CellState_t --> OutputGate
     OutputGate -->|o_t| a_t
   ```
   **门控计算**（$\sigma$为sigmoid）：  
   - 遗忘门：$f_t = \sigma(W_f \cdot [a_{t-1}, x_t] + b_f)$  
   - 输入门：$i_t = \sigma(W_i \cdot [a_{t-1}, x_t] + b_i)$  
   - 候选值：$\tilde{C}_t = \tanh(W_C \cdot [a_{t-1}, x_t] + b_C)$  
   - 细胞状态更新：$C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$  
   - 输出门：$o_t = \sigma(W_o \cdot [a_{t-1}, x_t] + b_o)$  
   - 隐藏状态：$a_t = o_t \odot \tanh(C_t)$  

#### **12.4.3 LSTM工作原理示例**
   - **任务**：  
     - $x_2=1$ 时：将 $x_1$ 值存入记忆  
     - $x_3=1$ 时：输出记忆值  
     - $x_2=-1$ 时：重置记忆  
   - **输入序列**：$x_1=[3,1,0,0], x_2=[1,0,1,0], x_3=[1,0,0,1]$  
     操作结果：记忆值累加→读取→重置  



**LSTM的优点**：  
+ 通过“加法”而非单纯“乘法”累积记忆，极大缓解了深层或长序列中的梯度消失/爆炸问题。
+ 可学习的门控机制，让模型自己决定“还要不要记住”、“要忘掉多少”、“对外输出多少”。
---

### **12.5 RNN/LSTM 应用场景**
1. **自然语言处理**  
   - 机器翻译（序列到序列建模）  
   - 情感分析（时序情感特征提取）  
2. **时序数据处理**  
   - 股票预测（捕捉历史趋势）  
   - 传感器异常检测  
3. **音频处理**  
   - 语音识别（声学模型）  
   - 音乐生成  

---

### **12.6 关键知识点总结**
| **概念**         | **核心功能**                              | **数学工具**                          |
|------------------|------------------------------------------|---------------------------------------|
| **记忆单元**     | 存储历史状态                              | $a_t=f(W_a a_{t-1} + W_x x_t + b)$   |
| **双向RNN**      | 同时捕获过去与未来信息                    | 正向+反向隐藏层联合输出               |
| **LSTM三门**     | 遗忘门/输入门/输出门控制信息流            | Sigmoid门控+Tanh变换                |
| **梯度问题解决** | 细胞状态 $C_t$ 的加法更新避免梯度消失      | $C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$ |








