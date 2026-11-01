# Movie Review Sentiment Analysis

基于 Kaggle 经典 NLP 教程 **Bag of Words Meets Bags of Popcorn**，完成电影评论情感分析项目，探索自然语言处理（NLP）中的文本预处理、词向量表示及机器学习分类方法。

## 1. Project Introduction

本项目使用电影评论数据集，对用户评论进行情感分类，判断评论表达的是正面情感还是负面情感。

项目主要学习如何将自然语言文本转换为计算机能够处理的数值特征，并利用机器学习模型完成情感分类。

## 2. Dataset

数据来源：Kaggle Word2Vec NLP Tutorial。

数据集包括：
- Labeled Training Data：25000 条带有情感标签的电影评论。
- Test Data：25000 条待预测的电影评论。
- Sample Submission：Kaggle 提供的提交格式示例。

训练数据包含三个主要字段：
- `id`：评论编号。
- `sentiment`：情感标签（0 表示负面，1 表示正面）。
- `review`：电影评论文本。

## 3. Main Workflow

### 3.1 Text Preprocessing

对原始电影评论进行文本清洗，包括：
- 去除 HTML 标签。
- 统一字母大小写。
- 去除标点符号及无关字符。
- 将文本转换为单词序列。

### 3.2 Word2Vec Word Embedding

使用 Gensim 中的 Word2Vec 模型训练词向量。

主要参数：
- Training method：Skip-gram
- Vector size：100
- Context window：5
- Epochs：10

模型最终建立了包含 28757 个词的词汇表。

通过 Word2Vec，将单词映射为 100 维向量，使具有相似上下文的词语能够在向量空间中体现一定的语义关系。

### 3.3 Average Word Vectors

将一条评论中所有能够找到对应词向量的单词进行向量求和，再计算平均值，得到整条评论的 100 维特征向量。

最终：
- 训练集特征矩阵：25000 × 100
- 测试集特征矩阵：25000 × 100

### 3.4 Sentiment Classification

使用 Scikit-learn 中的 Random Forest Classifier 进行情感分类。

主要参数：
- n_estimators：100
- random_state：42

利用训练集的评论特征及情感标签训练模型，并对测试集进行预测。

## 4. Prediction Results

模型成功完成 25000 条测试评论的情感预测。

预测结果：
- Negative reviews：12596
- Positive reviews：12404

## 5. Technologies

- Python
- Kaggle Notebook
- NumPy
- Pandas
- Gensim
- Scikit-learn
- NLP
- Word2Vec
- Random Forest

## 6. Learning Outcomes

通过本项目，初步了解了自然语言处理的基本流程，掌握了文本清洗、Word2Vec 词向量训练、平均词向量构建以及机器学习情感分类的基本方法。

同时，通过 Kaggle Notebook 实践，熟悉了在线 Notebook 环境、数据集管理和模型训练流程，并进一步理解了 Embedding 将离散文本转换为连续数值向量的基本思想。

## 7. Reference

Kaggle - Word2Vec NLP Tutorial:

https://www.kaggle.com/c/word2vec-nlp-tutorial/overview/part-1-for-beginners-bag-of-words
