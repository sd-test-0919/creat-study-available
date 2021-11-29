# ESMM
模型主要解决cvr建模的两个问题
- Sample Selection Bias (SSB) 传统CVR模型通常以点击数据为训练集，其中点击未转化为负例，点击并转化为正例。
  - 但是serving时，则是对整个空间的样本进行预估，而非只对点击样本进行预估
- Data Sparsity (DS) 作为CVR训练数据的点击样本远小于CTR预估训练使用的曝光样本。
## 模型
CTCVR和CTR的监督信息来训练网络，隐式地学习CVR其中CTR CTCVR都是使用了全部样本的
![image](https://user-images.githubusercontent.com/94423063/143899880-6ca26b63-9710-4484-929c-ae3a32b3227e.png)
  - 文中提出了为什么用乘建模CVR不用除
  - 真实场景预测出来的pCTR、pCTCVR值都比较小，“除”的方式容易造成数值上的不稳定
![image](https://user-images.githubusercontent.com/94423063/143899483-70da3195-eda7-425c-9676-b193350ade7f.png)
- 1）共享Embedding CVR-task和CTR-task使用相同的特征和特征embedding，即两者从Concatenate之后才学习各自部分独享的参数；
- 2）隐式学习pCVR 啥意思呢？这里pCVR（粉色节点）仅是网络中的一个variable，没有显示的监督信号。
- ![image](https://user-images.githubusercontent.com/94423063/143899929-847a92a9-c145-48ad-b0c8-507066f1b3e8.png)
