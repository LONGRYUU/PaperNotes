# Affective Image Classification using features inspired by psychology and art theory

方法：

- dimensional approach：将情感表示为2-3维的空间
- category approach：使用描述性的词语

以往方法的问题：

- 泛用的特征：设计专门编码情感的特征会带来更好的效果，但大部分工作使用的仍然是普适的特征
- 不统一的情感类别：情感类别的数量和层次理解不同
- 数据集：数据集大多未公开，并且没有标准
- 没有明确的评价指标

处理过程：

resize， crop， 从RGB转化到cylindrical coordinate color space，进行语义分割

因素：

- 颜色：饱和度以及亮度，色调，色彩，颜色统计，Itten Contrast
- 纹理：wavelet-based features，tamura纹理特征（粗糙度，对比度，方向性），灰度共生矩阵GLCM，
- 成分(composition)：详细程度，低的景深，主要的线条
- 内容(content)：人脸表情，皮肤



# Affective Image Content Analysis: A Comprehensive Survey

两大问题：情感gap和直觉的主观性

两种主要表示：CES和DES

CES：将情感用一些固定的类别标签表示

DES：用2维或3维笛卡尔空间表示

特征提取：手工设计，深度网络学习

情感分布学习

离散分布学习：SSL，WMMSSL，CPNN，WMMCPNN