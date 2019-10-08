## 目标检测

### Region Proposal + CNN

#### R-CNN

1. 输入图片
2. 截取ROI
3. 对每个Region用CNN提取特征
4. 用SVM对特征进行分类
5. 使用回归器修整框的大小

CNN是共享的，所以针对不同大小的Region需要通过corp或warp（裁剪或变形）放缩到同一尺寸

#### Fast R-CNN

1. 用CNN对整张图片提取特征
2. ROI Pooling层，使用简化的Spatial Pyramid Pooling保证输入到全连接层的数据维度大小一致
3. 使用Multi-task loss，将分类和回归问题一起训练，共享卷积层权重

#### Faster R-CNN

用**RPN**神经网络来搜索边缘



### 区域选择

#### selective search

使用基于图的图像分割法（Graph Based Image Segmentation）得到小的区域，然后逐步层次合并，生成大尺度的候选区域。

使用四个相似度评估指标，将四个相似度之和作为合并依据

- 颜色相似度：用L1范数归一化，获取每个颜色通道的25 bins直方图，共75维组成一个向量
- 纹理相似度
- 区域大小，优先合并小区域
- 区域距离，期望区域间距越小越好

给获得的区域打分：对于生成的区域，用生成顺序乘以随机数来打分，生成越早的原始权重越高；使用评分来选择区域

性能评估：计算生成区域与标准区域的ABO与MABO

#### Graph Based Image Segmentation

将像素作为顶点，将像素间的不相似度作为边。从小到大合并。

类内差异：类内不相似度最大的值

类间差异：类间不相似度最小的值

类间差异小于类内差异，则合并

### SPP-Net

Multi-View：对于一张图片，取多个crop进行测试，取平均值作为最终结果。

Multi-Size Training：用图中尺寸的输入来对模型进行训练，由于SPP池化层的存在，可以在一个网络中进行训练。

Full-Image Reprezentation：不进行crop裁剪，直接将完整的图片resize后输入模型训练。

缺点：Multi-stage训练，使用fine-tuning更新网络，spp层前的CNN层无法更新，需要大量空间存储特征值。

