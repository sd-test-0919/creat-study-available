# Vision Transformer
## 是基于transformer的cv领域应用
### model overview
![image](https://user-images.githubusercontent.com/94423063/142757280-89cac28a-d48a-4851-b971-15cef3beac62.png)
- 把图片分成固定大小的“patches”，线性embedding并对每个进行位置编码，作为一个标准transformer encoder的输入。类似于文本cls向量，在每个图片seq的前面添加一个\<cls> token

### 模型细节
- 基于经典的transformer处理一维文本数据，将二维图片变成一个展开的序列“patches”，每个patch对应于一个文本token。假设每个图片的分辨率是H\*W，pathes的分辨率是P\*P,序列长度N=H\*W\P^2。这个模型也学了整个图片的表示，预训练和finetune阶段都是一个分类head和图片表示的embedding相连，预训练的时候是一个隐层的mlp，finetune的时候是一个线性层。（为啥）
- 位置embedding一维和二维区别不大
- 简单介绍transformer encoder
- - 是multihead self attention block 和mlp block交替构成，每个block都由layer norm在前，残差连接在后
- mlp两层，包含GELU的非线性激活函数
- - ELU
- - GELU
- Inductive Bias
- ![image](https://user-images.githubusercontent.com/94423063/142762780-c0c923b2-7ccf-4416-95d5-d22eddbf3717.png)
- 主要是解释图片的分布的假设信息，vit比cnn使用的少很多，比如二维邻域结构，平移不变性等信息，位置信息都是从头学起，不过patches本身的做法就是带了conv-2d的设计的，mlp带了平移不变性，只是比之前cnn要更少一些
### Hybrid Architecture结构
- 论文中也给出了Hybrid Architecture，简单来说就先用CNN对图像提取特征，从CNN提取的特征图中提取patch embeddings，CNN已经将图像降采样了，所以patch size可以为1\*1
### 实验细节（TODO）
