# ArcFace和SphereFace以及CosineFace
Gradient domination的问题。 这个问题产生的原因是不同任务的loss的梯度相差过大， 导致梯度小的loss在训练过程中被梯度大的loss所带走
## SphereFace
![image](https://user-images.githubusercontent.com/94423063/144701837-35b9b11c-cd66-44b8-b10c-40e3304faed5.png)
- 使用m放大同类间隔
- 假设最后一个全连接层中的线性变换矩阵可以用作角度空间中类中心的表示，并以乘法的方式惩罚深层特征与其相应权重之间的角度
## CosineFace
![image](https://user-images.githubusercontent.com/94423063/144702911-b2b52595-424f-420c-ae4e-37e7a5b3de08.png)

## ArcFace
![image](https://user-images.githubusercontent.com/94423063/144700707-4c8fc13a-9890-424e-b162-83b5dffed1d7.png)
- 基础的softmax，将b设为0
![image](https://user-images.githubusercontent.com/94423063/144701074-30a835c9-5030-449f-88a5-8d5e72823d7f.png)
- w和x都使用l2正则，s用来缩放
![image](https://user-images.githubusercontent.com/94423063/144701608-8a1f3aff-fad9-4963-aaf4-d96e0f386125.png)
![image](https://user-images.githubusercontent.com/94423063/144701627-e1cd667a-79fc-432f-adb8-35584bcbceb5.png)
- 引入了角度margin m加强类内相似性和类间差距，弧长变短
![image](https://user-images.githubusercontent.com/94423063/144702967-bf5870c4-ed95-4ade-bf7c-e5f63577734b.png)
- theta1和theta2指二分类的类内间隔
![image](https://user-images.githubusercontent.com/94423063/144703049-877339b6-3f94-4f5a-83c3-96a54f976aaf.png)
