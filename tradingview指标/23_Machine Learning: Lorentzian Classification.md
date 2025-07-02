https://www.tradingview.com/v/WhBzgfDu/



![image-20250701155143161](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011551235.png)

█ 概述

洛伦兹距离分类器（LDC）是一种能够对多维特征空间中的历史数据进行分类的机器学习算法。本文指标展示了，当洛伦兹距离作为一种新颖的近似最近邻（ANN）算法的距离度量时，洛伦兹分类同样可用于预测未来价格走势的方向。

█ 背景

在物理学中，洛伦兹空间以其在爱因斯坦广义相对论中描述时空曲率的作用而著称（2）。然而，这一理论物理中的抽象概念，在交易领域也展现出了实际应用价值。

近期，有学者提出洛伦兹空间同样适用于时间序列数据分析（4）、（5）。多项实证研究表明，洛伦兹距离在应对异常值和噪声方面较常用的欧氏距离更具鲁棒性（1）、（3）、（6）。此外，洛伦兹距离在多种距离度量（如曼哈顿距离、Bhattacharyya相似度和余弦相似度）中表现优越（1）、（3）。除动态时间规整（DTW）方法外（遗憾的是目前PineScript计算量过大无法实现），洛伦兹距离在多样的时间序列数据集上均展现出最高的平均准确率（1）。

欧氏距离常作为基于最近邻搜索算法的默认距离度量，但在处理金融市场数据时并非总是最优选择。原因在于，金融市场数据极易受到全球重大事件（如FOMC会议、“黑天鹅”事件）影响。这种基于事件的数据畸变，可类比为大质量物体对时空的引力扭曲。对于金融市场而言，类似被扭曲的连续体可称为“价格-时间”。

下图对比了三维欧氏空间与洛伦兹空间中，相似历史点的邻域分布：

![image-20250701155208114](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011552184.png)

该图显示，洛伦兹空间能更好地适应价格-时间的扭曲。洛伦兹距离函数压缩了欧氏邻域，使得洛伦兹空间中新邻域分布不仅聚集于原点，也集中于各主要特征轴。这意味着，虽然部分最近邻在不同距离度量下相同，洛伦兹空间却能纳入欧氏距离下无法考虑的历史点。

从直观上看，洛伦兹距离的优势也合乎逻辑。例如，鲍威尔主席发表演讲后数小时内的价格行为，很可能与以往其演讲后的一些时段相似，无论当时市场是否超买/超卖，或宏观环境偏多/偏空。这些历史参考点对预测模型极具价值，而欧氏距离往往遗漏这些邻居，反而偏向无关的数据点。采用洛伦兹距离，机器学习模型能够考虑事件导致的价格-时间扭曲，从而突破时间序列带来的时序偏差。

有关本指标所用近似最近邻（ANN）算法的实现细节，请参见源代码中的详细注释。

█ 使用说明

以下为本指标界面各部分的说明：

![snapshot](https://www.tradingview.com/x/KvBK83xf/)

以下为本指标各项设置的说明：

![snapshot](https://www.tradingview.com/x/mSBGsh3B/)

**通用设置：**

- Source（数据源）——默认值为“hlc3”，用于控制输入数据源。
- Neighbors Count（邻居数量）——默认8，最小1，最大100，步长1。用于设置考虑的邻居数量。
- Max Bars Back（最大回溯K线数）——默认2000。
- Feature Count（特征数量）——默认5，最小2，最大5。用于控制机器学习预测的特征数量。
- Color Compression（色彩压缩）——默认1，最小1，最大10。用于调整色阶强度的压缩因子。
- Show Exits（显示离场）——默认false。控制是否在图表上显示离场阈值。
- Use Dynamic Exits（动态离场）——默认false。控制是否基于核回归动态调整离场阈值以尽可能延长盈利。

**特征工程设置：**  
注：本部分用于微调参与机器学习预测的特征。默认参数针对4H~12H周期优化，亦适用于其他周期。模型默认支持带两个参数的特征（参数A和B）。即便仅有4种特征，设置不同也视为不同特征。若特征仅需一个参数，则第二参数默认为基于EMA的平滑（默认1）。这些特征组合为测试中表现最优，未来可增加更多选项。

- Feature 1——默认“RSI”，可选：“RSI”、“WT”、“CCI”、“ADX”
- Feature 2——默认“WT”，可选同上
- Feature 3——默认“CCI”，可选同上
- Feature 4——默认“ADX”，可选同上
- Feature 5——默认“RSI”，可选同上

**过滤器设置：**

- Use Volatility Filter（波动率过滤）——默认true。控制是否启用波动率过滤器。
- Use Regime Filter（趋势过滤）——默认true。控制是否启用趋势检测过滤器。
- Use ADX Filter（ADX过滤）——默认false。控制是否启用ADX过滤器。
- Regime Threshold（趋势阈值）——默认-0.1，最小-10，最大10，步长0.1。用于检测趋势/震荡市场的趋势检测过滤器。
- ADX Threshold（ADX阈值）——默认20，最小0，最大100，步长1。用于检测趋势/震荡市场的ADX过滤阈值。

**核回归设置：**

- Trade with Kernel（核交易）——默认true。控制是否启用核交易。
- Show Kernel Estimate（显示核估计）——默认true。控制是否显示核估计。
- Lookback Window（回溯窗口）——默认8，最小3。用于核估计的K线数量。推荐范围：3-50。
- Relative Weighting（相对权重）——默认8，步长0.25。用于控制不同周期的相对权重。推荐范围：0.25-25。
- Start Regression at Bar（回归起始K线）——默认25。用于设置回归起始K线索引。推荐范围：0-25。

**显示设置：**

- Show Bar Colors（显示K线颜色）——默认true。控制是否显示K线颜色。
- Show Bar Prediction Values（显示K线预测值）——默认true。控制是否以整数形式显示每根K线的模型评估值。
- Use ATR Offset（使用ATR偏移）——默认false。控制是否使用ATR偏移替代K线预测偏移。
- Bar Prediction Offset（K线预测偏移）——默认0，最小0。用于设置预测偏移百分比，以K线高点或收盘价为基准。

**回测设置：**

- Show Backtest Results（显示回测结果）——默认true。控制是否显示当前配置的胜率。

---

█ 参考文献

(1) R. Giusti 和 G. E. A. P. A. Batista, “An Empirical Comparison of Dissimilarity Measures for Time Series Classification,” 2013年巴西智能系统会议，2013年10月，DOI: 10.1109/bracis.2013.22。  
(2) Y. Kerimbekov, H. Ş. Bilge, 和 H. H. Uğurlu, “The use of Lorentzian distance metric in classification problems,” Pattern Recognition Letters, 84卷, 170–176, 2016年12月, DOI: 10.1016/j.patrec.2016.09.006。  
(3) A. Bagnall, A. Bostrom, J. Large, 和 J. Lines, “The Great Time Series Classification Bake Off: An Experimental Evaluation of Recently Proposed Algorithms.” ResearchGate, 2016年2月4日。  
(4) H. Ş. Bilge, Yerzhan Kerimbekov, 和 Hasan Hüseyin Uğurlu, “A new classification method by using Lorentzian distance metric,” ResearchGate, 2015年9月2日。  
(5) Y. Kerimbekov 和 H. Şakir Bilge, “Lorentzian Distance Classifier for Multiple Features,” 第六届国际模式识别应用与方法会议论文集, 2017, DOI: 10.5220/0006197004930501。  
(6) V. Surya Prasath 等, “Effects of Distance Measure Choice on KNN Classifier Performance - A Review.” [在线]。

---

█ 致谢

[veryfid](https://www.tradingview.com/u/veryfid/) —— 提供了诸多宝贵见解、讨论与建议，对本项目的形成有重要帮助。  
[capissimo](https://www.tradingview.com/u/capissimo/) —— 其关于PineScript中多种KNN实现的开源思路为本项目的最初构想提供了灵感。  
[RikkiTavi](https://www.tradingview.com/u/RikkiTavi/) —— 在物理相关话题上的深入交流，以及帮助开发了用JavaScript可视化三维距离算法的机制。  
[jlaurel](https://www.tradingview.com/u/jlaurel/) —— 推荐了许多关键文献，助力我深入理解本项目相关主题。  
[annutara](https://www.tradingview.com/u/annutara/) —— 协助指标Beta测试，并在早期提出了众多有益建议与见解。  
[jasontaylor7](https://www.tradingview.com/u/jasontaylor7/) —— 协助指标Beta测试，并通过多次交流优化了回测流程。  
[meddymarkusvanhala](https://www.tradingview.com/u/meddymarkusvanhala/) —— 协助指标Beta测试。  
[dlbnext](https://www.tradingview.com/u/dlbnext/) —— 对指标进行了极为详尽的回测，并提出了大量改善用户体验的建议。

---












































































