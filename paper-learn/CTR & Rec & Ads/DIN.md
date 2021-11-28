# DIN模型 
DIN方法基于对用户历史行为数据的两个观察
- 1、多样性，一个用户可以对多种品类的东西感兴趣；
- 2、部分对应，只有一部分的历史数据对目前的点击预测有帮助，不同的广告对应的同一用户兴趣表示向量不同，
- 此外，还提出了 mini-batch aware regularization && data adapative activation function。 

## 用户特征
用 one hot 或 multi-hot表示
## 模型结构
![image](https://user-images.githubusercontent.com/94423063/143725902-1e377a78-a2a1-45ad-8a15-d5a2993050f2.png)
### 模型区别与base DNN的两个设计点
- activation units
- ![image](https://user-images.githubusercontent.com/94423063/143729743-de186a41-5dd8-4f39-981e-a9afea156f9f.png)
- 输入
  - user behavior embedding vector;
  - ad embedding vector;
  - 前面两个的out product(外积)   
最后得到activation weight乘在序列的user embedding上  
- 最后提出了尝试过 LSTM 对用户历史行为数据进行建模。但它没有显示出任何改善。与 NLP 任务中受语法约束的文本不同
  - 用户历史行为序列可能包含多个并发兴趣。对这些兴趣的快速跳跃和突然结束导致用户行为的序列数据看起来很嘈杂。一个可能的方向是设计特殊的结构来以序列方式对此类数据进行建模。
## mini-batch aware regularization
## data adapative activation function
是对PReLU的改良
PReLU的问题
- 整流点在0附近，两侧的概率是0/1
![image](https://user-images.githubusercontent.com/94423063/143731648-e5467386-5fe5-4cc9-a249-13707da0e390.png)
- 整流点在均值附近
- 概率是经过一个sigmoid函数的计算
