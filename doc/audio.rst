音频分析笔记
=====================
正弦波
---------------------
概念
~~~~~~~~~~~~~~~~~~~~~~
**采样率** （也称为采样速度或者采样频率）定义了每秒从连续信号中提取并组成离散信号的采样个数，它用赫兹（Hz）来表示。 采样频率的倒数叫作采样周期或采样时间，它是采样之间的时间间隔。 注意不要将采样率与比特率（bit rate，亦称“位速率”）相混淆。

**位深** 也被称为采样精度，单位为Bit,常见的位数选择有16Bit,24Bit。前面说每秒钟所采样样本的总数目是采样率，每个样本中信息的比特数就是位深。

::

    Bits（音频大小）=采样率 * 位深 * 通道数 * 时间（秒）
