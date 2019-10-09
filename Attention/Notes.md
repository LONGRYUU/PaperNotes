# An Attentive Survey of Attention Models

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

