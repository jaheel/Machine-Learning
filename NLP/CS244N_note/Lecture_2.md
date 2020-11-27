# Word Vectors

## Word meaning

one-hot vectors: 单词标为1，其他全为0的向量

distributional similarity(分布相似性)：表示某个变量值，注意上下文

> 统计各种例句中 与 该词汇 一同出现的其他词汇的频率



给每一个单词构造密集型向量

> 让它可以预测目标单词所在文本的其他词汇
>
> 运用 上述 分布相似性



## Word2vec introduction

**Basic idea of learning neural network word embeddings**

We define a model that aims to predict between a center word $w_t$ and context words in terms of word vectors 
$$
p(context|w_t) = ...
$$
which has a loss function, e.g.,($w_t$ 是中心词汇，$w_{-t}$是除它外所有其他的上下文)
$$
J = 1-p(w_{-t}|w_t)
$$
We look at many positions $t$ in a big language corpus

We keep adjusting the vector representations of words to minimize this loss



**Main idea of word2vec**

Predict between every word and its context words



Two algorithm

* Skip-grams(SG)

  > Predict context words given target (position independent)

* Continuous Bag of Words(CBOW)

  > Predict target word from bag-of-words context



**Softmax function: Standard map from $\R^V$ to a probability distribution**





## Research highlight

## Word2vec objective function gradients



## Optimization refresher

## Assignment 1 notes

## Usefulness of word2vec

