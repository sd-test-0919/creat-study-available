# swin transformer
相比于自然语言，视觉多实体且分辨率高，针对这种区别，提出了用滑窗计算表示的多层的transformer，滑窗结构通过限制自注意力计算在局部window内，同时允许跨window的交叉连接，计算复杂度和图片大小是线性的。
# 模型整体结构
![image](https://user-images.githubusercontent.com/94423063/143673823-da47688a-313b-4258-bd9b-932cb3baa057.png)
模型一共包含4个Stage，每个stage都会缩小输入特征图的分辨率
- 第一步和vit相同，Patch Embedding
- 在每个Stage里，由Patch Merging和多个Block组成。
- Patch Merging：降低图片分辨率，节省一定运算量。
  - 计算量公式推导这个讲的很清楚：https://blog.csdn.net/weixin_39778049/article/details/116020969
- Block：由LayerNorm，MLP，Window Attention 和 Shifted Window Attention组成。
Patch Merging:
- 比较简单，如图，最后用全连接降维
![image](https://user-images.githubusercontent.com/94423063/143674093-172ed875-83d7-42fc-be06-84717da1eba4.png)
# window attention 和 shift window attention
## window attention
- 利用cnn的window概念减少global attention的参数量，除了相对位置编码以外和普通attention一样
- relative_position_bias 
-  2*(wh, ww) 2:代表坐标是2维（x,y）
-  2, Wh\*Ww
-  [2, wh\*ww, 1] 和 [2, 1, wh\*ww]，进行广播相减
-  最终得到 2, wh\*ww, wh\*ww 形状的张量
-  将(x，y)展开为一维，将x,y坐标相加转换为一维，偏移量是相等的。
-  所以针对其中一维乘2 * self.window_size[1] - 1，在最后一维上进行求和，成为一个不参与训练
   - 如果乘以小于window\_size，得到的是序列token的相对位置偏移量，忽略图片本身存在的空间位置信息
   - 如果乘以的数值大于window\_size，小于(2 * window\_size - 1)，空间中相对位置不对；
   - 如果乘以的数值大于(2 * window\_size - 1)，可以保证空间位置信息，但是造成了参数量增加，并且存在没有利用的参数。 
## shift window attention
- 可参考https://zhuanlan.zhihu.com/p/367111046
  - 把9window -> 4window如何旋转，如何计算mask介绍的很清楚细致
