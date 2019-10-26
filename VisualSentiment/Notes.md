>>>>>>> # Affective Image Classification using features inspired by psychology and art theory
>>>>>>>
>>>>>>> 方法：
>>>>>>>
>>>>>>> - dimensional approach：将情感表示为2-3维的空间
>>>>>>> - category approach：使用描述性的词语
>>>>>>>
>>>>>>> 以往方法的问题：
>>>>>>>
>>>>>>> - 泛用的特征：设计专门编码情感的特征会带来更好的效果，但大部分工作使用的仍然是普适的特征
>>>>>>> - 不统一的情感类别：情感类别的数量和层次理解不同
>>>>>>> - 数据集：数据集大多未公开，并且没有标准
>>>>>>> - 没有明确的评价指标
>>>>>>>
>>>>>>> 处理过程：
>>>>>>>
>>>>>>> resize， crop， 从RGB转化到cylindrical coordinate color space，进行语义分割
>>>>>>>
>>>>>>> 因素：
>>>>>>>
>>>>>>> - 颜色：饱和度以及亮度，色调，色彩，颜色统计，Itten Contrast
>>>>>>> - 纹理：wavelet-based features，tamura纹理特征（粗糙度，对比度，方向性），灰度共生矩阵GLCM，
>>>>>>> - 成分(composition)：详细程度，低的景深，主要的线条
>>>>>>> - 内容(content)：人脸表情，皮肤
>>>>>>>
>>>>>>> 
>>>>>>>
>>>>>>> # Affective Image Content Analysis: A Comprehensive Survey
>>>>>>>
>>>>>>> 两大问题：情感gap和直觉的主观性
>>>>>>>
>>>>>>> 两种主要表示：CES和DES
>>>>>>>
>>>>>>> CES：将情感用一些固定的类别标签表示
>>>>>>>
>>>>>>> DES：用2维或3维笛卡尔空间表示
>>>>>>>
>>>>>>> 特征提取：手工设计，深度网络学习
>>>>>>>
>>>>>>> 情感分布学习
>>>>>>>
>>>>>>> 离散分布学习：SSL，WMMSSL，CPNN，WMMCPNN
>>>>>>>
>>>>>>> # StyleNet: Generating Attractive Visual Captions with Styles
>>>>>>>
>>>>>>> 核心思想：factored-LSTM，将语言生成模块的LSTM中的输入权重矩阵W分解为USV，其中S可以替换为不同风格的因素。
>>>>>>>
>>>>>>> 多任务训练：
>>>>>>>
>>>>>>> - 根据Image Caption训练集，生成事实描述；
>>>>>>> - 作为语言模型训练
>>>>>>>
>>>>>>> 两个任务的参数共享，除了上述的S矩阵
>>>>>>>
>>>>>>> 
>>>>>>>
>>>>>>> # “Factual” or “Emotional”: Stylized ImageCaptioning with Adaptive Learning andAttention
>>>>>>>
>>>>>>> factual-style LSTM
>>>>>>>
>>>>>>> 核心思想：用不同的参数表示factual和style因素，获取二者间的内在联系，使用attention机制将二者结合在一起。即保留原始的Wx和Wh作为事实描述参数，而降Sx和Sh作为风格化参数，用一个动态attention权重在每个时间点将二者加权求和
>>>>>>>
>>>>>>> adaptive learning：类似Knowing when to look，采用动态的attention机制，根据当前的词汇来决定是否应用attention机制。
>>>>>>>
>>>>>>> 二阶段训练：先冻结S矩阵，仅针对事实性描述进行训练；第二阶段则使用风格化描述训练S
>>>>>>>
>>>>>>> 为了解决风格化描述不足的问题，设计了特殊的损失函数，当输出词语是风格化相关词语时，用MLE损失衡量；否则用KL散度度量生成词语与事实性模型生成词语的差别，期望KL散度小。
>>>>>>>
>>>>>>> 
>>>>>>>
>>>>>>> # SemStyle: Learning to Generate Stylised Image Captions using Unaligned Text
>>>>>>>
>>>>>>> 
>>>>>>>
>>>>>>> 将语义信息和风格信息分离
