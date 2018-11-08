# 1. 常用数据集：
+ criteo数据集: http://labs.criteo.com/2014/02/kaggle-display-advertising-challenge-dataset/
+ MovieLens: https://grouplens.org/datasets/movielens/latest/
+ AT&T人脸数据:  https://files.cnblogs.com/files/king-lps/att_faces.zip

# 2.【2017-WWW】Neural Collaborative Filtering --- NeuMF神经矩阵分解模型

+ 摘要
    + 本文提出一种基于神经网络的协同过滤NCF。
    + 在推荐系统中，当前的很多工作应用深度学习对一些辅助信息进行建模，比如item的文本描述、音乐的声学特征。
    + 但是对CF中的核心问题：对user和item之间的交互进行建模。deeplearning仍然依赖于矩阵分解，并且在user和item的隐向量上应用内积。
    + 本文提出一个框架NCF，它用神经架构替换inner product

+ 介绍
    + 提出了一个神经网络架构，用于对user-item的隐向量建模，并且发明了一个一般性的框架NCF用于协同过滤
    + 本文证明了MF可以理解为NCF的特例。并且使用MLP来赋予NCF高level的非线性
    + 在两个real-world数据集上做了大量实验，结果证明了NCF的有效性，并且展示了神经网络做协同过滤的希望。
+ 举证分解 
    ![IMAGE](/images/blog/recsys_paper/7B1446EAB408C6D4626E2656E9194DF7.jpg)
    ![IMAGE](/images/blog/recsys_paper/6408FE36F565AD57E77F816142F2477C.jpg)


# 3.【2018-KDD】 Learning Tree-based Deep Model for Recommender Systems --- 阿里的TDM

+ 摘要




# 4. 【2017-IJCAI】Deep Matrix Factorization Models for Recommender Systems

+ 摘要
本文提出了一个新的基于神经网络的矩阵分解模型架构。首先，构造一个Usre-Item矩阵，它带有显示的评分和非偏的隐式的反馈。将这个矩阵作为输入，本文提出了一个深度的学习架构，来学习一个
通用的低维空间用于user和item的表示。其次，本文设计了一个新的loss function，它基于binary交叉熵，其考虑了显示的评分和隐式的反馈，可以更好的优化。

+ Introduction
在本文中，为了利用明确的ratings和隐反馈，我们提出了一中神经矩阵模型用于top-N推荐。我们首先构造一个User-Item矩阵，它和其他相关的方法不同（它们仅仅用到了显示的评分或者隐式的反馈）。
将这个矩阵作为输入，提出了一个神经网络架构用于学习一个通用的隐藏的低维空间来表示user和item。


+ DMF模型架构
![IMAGE](/images/blog/recsys_paper/8C649289255F996C536197CE7956D637.jpg)

+ Loss Function
    + Squared Loss:
        ![IMAGE](/images/blog/recsys_paper/0ECEF10C1F06A4856BE9F6DDE0C282CB.jpg) 
    + Cross Entropy
        ![IMAGE](/images/blog/recsys_paper/1435197F300964FAA0497D792AED95C7.jpg)
    + NCE(本文提出的，跟NCE不一样)
        ![IMAGE](/images/blog/recsys_paper/24DFD94C474A4CEAF261521B8988EF89.jpg)

    其中，![IMAGE](/images/blog/recsys_paper/575BB0280B690F406D068F538CEF42A8.jpg) 是原始的评分矩阵。


# 5.【ICML-2015 workshop】Siamese Neural Networks for One-shot Image Recognition ---孪生网络

+ 论文链接：https://www.cs.cmu.edu/~rsalakhu/papers/oneshot1.pdf
+ 参考链接：https://www.cnblogs.com/king-lps/p/8342452.html

![IMAGE](/images/blog/recsys_paper/D2F4C8269DAE423540F366F4B4DBF745.jpg)




# 6. 【NIPS-2005】Learning a Similarity Metric Discriminatively, with Application to Face Verification ---孪生网络


# 7. 【CVPR-2015】FaceNet: A Unified Embedding for Face Recognition and Clustering --- Triplet Loss，google的论文

+ 论文链接：https://arxiv.org/pdf/1503.03832.pdf
+ 基本思想：
    + Triplet Loss最早在FaceNet的论文中提出，用来学习人脸的向量表示。简单来说，triplet loss的目标是：
        - 两个具有同样标签的样本，他们在新的编码空间里距离很近。
        - 两个具有不同标签的样本，他们在新的编码空间里距离很远。
    ![IMAGE](/images/blog/recsys_paper/49DDB2A0C60DAF9D868ECDE35C532C37.jpg)

+ 摘要：
    在人脸识别场景中，已经有很多经典的工作了。本文提出一个系统，叫做FaceNet，它能够直接学习到一个映射：人脸图片到一个dense的欧氏空间，其中距离可以直接对应于人脸相似度。一旦这个空间产生了，那诸如人脸识别、验证、聚类都可以简单地实现。
    我们的模型直接train深度卷积神经网络来优化embedding，而不是像以前的工作一样，使用一个中间的瓶颈layer。对于train，我们使用triplet，。我们的方法的好处是更加有效的表示性：我们得到了state-of-the-art的人脸识别表现，尽管我们只使用了128-bytes/人脸。
    在广泛被使用的数据集LFW(Labeled Faces in the Wild)上，我们的系统得到了一个新的记录accuracy 99.63%。在YouTube Faces DB上得到了95.12%。我们的系统比目前最好 的结果，错误率降低了30%。
    我们也引入了harmonic embedding的概念，和harmonic(和声的) triplet loss，它描述了人脸embedding的不同版本。


+ Triplet Loss
    ![IMAGE](/images/blog/recsys_paper/6CCB412D38C1E6860FE9AE19809A1E52.jpg)
    ![IMAGE](/images/blog/recsys_paper/7D7126E096AC4610F706154D756F916E.jpg)

    embedding表示成为： ![IMAGE](recsys_paper/6BBAE6C267F80E126B36BCA3B15534CA.jpg) ，它将一个图片x映射到d维的欧氏空间。此外，我们限制这个embedding到d维的超球体，也就是说 ![IMAGE](recsys_paper/F5A30B28FDD62E2FB9D67815F26FBC05.jpg)，
    
    考虑一个三元组（Triplet）:
    + anchor（基准正例）
    + a positive of the same class as the anchor（正例）
    + a negative of a different class（负例）
    
    三元组的表示分别为：![IMAGE](/images/blog/recsys_paper/6C7572933678F49166486DBB457E4BAE.jpg)，我们希望：
    
    ![IMAGE](/images/blog/recsys_paper/CF9172729F2820C491B3F1AE61FE5CBA.jpg)
    
    其中，![IMAGE](/images/blog/recsys_paper/9DF77483D94C9B7306831F3D1E2F0E68.jpg) 表示正负例的边界，整体就是max margin的思想。所以Triplet loss定义为：
    ![IMAGE](/images/blog/recsys_paper/1E9C1E5C94DC742700F154916CC64A0B.jpg)