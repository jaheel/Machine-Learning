# Bayesian network

贝叶斯网，又称“信念网”(belief network)

借助有向无环图(Directed Acyclic Graph, DAG)来刻画属性之间的依赖关系

使用条件概率表(Conditional Probability Table, CPT)来描述属性的联合概率分布



边际独立性(marginal independence)

条件独立性(conditional independence)

## 结构

$$
P_B(x_1,x_2,\dotsb,x_d) = \prod_{i=1}^d {P_B(x_i|\pi_i)} = \prod_{i=1}^d \theta_{x_i|\pi_i}
$$

## D-separation

有向分离：为了分析有向图中变量间的条件独立性

* 找出有向图中所有V型结构，在V型结构的两个父节点之间加上一条无向边
* 所有有向边改为无向边

产生的无向图称为“道德图”(moral graph)，令父节点相连的过程称为“道德化”(moralization)



## 学习

评分函数：
$$
s(B|D)=f(\theta)|B|- LL(B|D) \\
|B|:贝叶斯网参数个数 \\
f(\theta):描述每个参数\theta所需的字节数 \\
LL(B|D) = \sum_{i=1}^m \log{P_B(x_i)}
$$


学习任务转化为一个优化任务：寻找一个贝叶斯网B使评分函数s(B|D)最小



若$f(\theta)=1$，每个参数用1字节描述，则得到AIC(Akaike Information Criterion)评分函数：
$$
AIC(B|D) = |B|-LL(B|D)
$$
若$f(\theta)= \frac{1}{2} \log m$，则得到BIC(Bayesian Information Criterion)评分函数：
$$
BIC(B|D)= \frac{\log m}{2}|B| - LL(B|D)
$$
显然，$f(\theta)=0$，评分函数退化为负对然似然，学习任务退化为极大似然估计。



参数$\theta_{x_i|\pi_i}$能直接在训练数据D上通过经验估计获得：
$$
\theta_{x_i|\pi_i} = \hat{P_D}(x_i|\pi_i)
$$

## 推断(inference)

通过已知变量观测来推测待查询变量的过程称为“推断”(inference)

已知变量观测值称为”证据“(evidence)



最理想的是直接根据贝叶斯网定义的联合概率分布来精确计算后验概率（NP难问题）

变通：”近似推断“；使用吉布斯采样(Gibbs sampling)来完成（随机采样方法）





## reference

[网页链接](https://www.cnblogs.com/LittleHann/p/11683607.html)

周志华 《机器学习》