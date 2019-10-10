# An Attentive Survey of Attention Models



#### 优点：

- 性能优良，在多个任务上达到SOTA
- 增强模型的可解释性
- 克服随着输入长度增长带来的性能下降
- 提高序列的计算效率



#### 传统模型的问题：

- 将长序列压缩到固定长度的序列可能引起信息的损失
- 难以在输入和输出之间进行有效对齐

对于seq2seq任务，输出期望被输入的特定部分影响更多，而模型缺少这样一个选择相关输入的机制。



#### Attention Model：

学习每个encoder与decoder的隐藏状态h与s直接的关联性，从而为每个h分配权值，将所有h向量加权作为decoder输入



### 模型类别

#### Number of Sequences

**distinctive**：编码器和解码器对应的隐藏状态属于不同的序列

例子：机器翻译，文本摘要，图像描述，语音识别。

**co-attention**：同时处理多个输入序列，共同学习其权重以捕获其中的内在联系。

例子：Visual Question Answering，图像特征和问题向量互相引导对方的Attention权重学习

**self-attention**：编码器和解码器对应的隐藏状态属于相同的序列，即学习输入序列中词语间的相关性

例子：推荐系统，文本分类

#### Number of Abstractions

**single-level**：仅对输入进行attention权重学习

**multi-level**：按照抽象层次，多次运用attention机制

例子：top-down attention，bottom-up attention，attention-via-attention，HAM：捕获文档中重要的句子，捕获句子中重要的单词

#### Number of Positions

**soft-attention**：在输入上全局地进行学习，获取权重

**hard-attention**：对输入进行随机采样，然后进行权重学习，降低了计算开销，但是使得框架不可微，难以优化

**local-attention**：介于soft和hard-attention机制之间，先选择进行attention学习的区域，然后在该区域进行soft-attention权重学习

#### Number of Representations

**multi-representational**：将输入进行多重表示，用attention机制为不同的表征分配权重。

**multi-dimensional**：在输入的特征向量上进行权重分配，根据上下文环境为词语分配权重，解决一词多译的问题

### 使用Attention的网络结构

#### Encoder-Decoder

attention模型能够将各种尺寸的输入转化为固定大小的向量，从而使输入和输出解耦。例如图像描述、VQA等；对于离散的输出，譬如Pointer Network，使用attention模型来给出各个输入点被选择的权重作为其概率。

#### Memory Network

#### Networks without RNNs

Position-wise FNN,Multi-head self-attention





# Spatial Transformer Networks

### Spatial Attention

获得表示的空间变换不变性

### Localization Network

根据输入的特征图获取变换的参数（回归）

### Parameterized Sampling Grid

使用上一层网络生成的参数，获取采样网格区域对应的输入区域，

### Differentiable Image Sampling





# Squeeze-and-Excitation Networks

### Channel Attention

将卷积视为信号的分解，将时域上的一个信号分解为频域上的多个分量

不同的分量（通道）的重要程度显然是不一样的，所以可以对不同的channel分配不同的权重

浅层次的SE结构着重于关注低层次、类别不明的特征，而位于深层次的SE结构则会关注类别明确的特定特征。

#### Deeper architectures

resnet skip connections, highway networks,multi-branch convs,grouped convs

#### Algorithmic Architecture Search

SE块可以用于加速强化学习

### 模型

Transform(卷积) ->squeeze->excitation

#### squeeze

对全局信息进行嵌入编码

通过对每个通道的特征图进行全局平均池化，将所有局部信息整合到一起，输出一个C维的向量

#### excitation

学习通道间的非线性关系，并且保证可以对多个通道分配权重，而不仅仅像one-hot一样关注一个通道，输出为C维向量S

#### scale

将输出的S每一维的权重用于放缩对应的每一个通道的特征图，从而得到模块的最终输出

