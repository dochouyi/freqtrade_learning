https://www.tradingview.com/v/o50NYLAZ/

# AlphaTrend

![image-20250702110403980](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507021104053.png)



Mar 24, 2022

AlphaTrend 是我个人基于 Trend Magic 衍生且仍在开发中的全新指标：

![Trend Magic](https://s3.tradingview.com/k/kRIjThLZ_mid.png)

在 Magic Trend 中存在一些问题，AlphaTrend 旨在解决这些问题，包括：

1. 最小化止损并应对震荡市况。
2. 在趋势市中提供更为准确的买/卖信号。
3. 提供显著的支撑与阻力位。
4. 融合来自不同类别、彼此兼容的指标，形成关于动量、趋势、波动率、成交量及移动止损的有意义组合。

基于上述目标，AlphaTrend 具有以下特性：

1. 在震荡市中表现为“死指标”，如其前身 Magic Trend，不会频繁给出虚假信号。
2. 通过一条相对于主线偏移2根K线的辅助线，AlphaTrend 可通过两线交叉生成买卖信号。

- 当 AlphaTrend 主线向上穿越其偏移线，且两线间填充为绿色时，发出买入/做多信号。
- 当 AlphaTrend 主线向下穿越其偏移线，且两线间填充为红色时，发出卖出/做空信号。

3. AlphaTrend 线的作用：
   - 在上升趋势中，主线以距离K线最低价1倍ATR（默认系数）作为支撑位，并作为移动止损线。
   - 在下降趋势中，主线以距离K线最高价1倍ATR（默认系数）作为阻力位，并作为移动止损线。
   - AlphaTrend 线越平直，支撑与阻力作用越强。

4. Trend Magic 计算中采用CCI，AlphaTrend 则以MFI作为动量指标。但当无成交量数据时，MFI 值为0，因此提供了一个按钮，在勾选相关选项后可切换为RSI计算，以解决无成交量数据时的适用性问题。
   - 动量：RSI 与 MFI
   - 趋势：Magic Trend
   - 波动率：ATR
   - 移动止损：ATR Trailing Stop
   - 成交量：MFI

AlphaTrend 实质上是多种指标的结合体。

默认参数：
- 系数：1（ATR移动止损的倍数因子）
- 通用周期：14（ATR、MFI及RSI的计算周期）



































