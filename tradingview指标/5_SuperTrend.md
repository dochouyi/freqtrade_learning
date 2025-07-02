https://www.tradingview.com/v/r6dAP7yi/

# SuperTrend

![image-20250702103330990](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507021033066.png)



SuperTrend 是最常见的基于 ATR 的跟踪止损指标之一。

在本版本中，您可以在设置中更改 ATR 的计算方法。默认方法为 RMA，另一种可选方法为 SMA。

该指标易于使用，并能准确反映当前趋势。其构建基于两个参数：周期和乘数。默认值分别为平均真实波幅（ATR）或交易周期的 10，以及乘数的 3。

平均真实波幅（ATR）在“SuperTrend”指标中起着关键作用，因为该指标正是利用 ATR 来计算其数值。ATR 指标反映价格波动的幅度。

当指标开始绘制在收盘价上方或下方时，会生成买入或卖出信号。当“SuperTrend”收于价格上方时，生成买入信号；当其收于收盘价下方时，生成卖出信号。

这也表明趋势正由下跌转为上升。反之，当“SuperTrend”收于价格上方时，指标颜色变为红色，生成卖出信号。

“SuperTrend”指标可应用于股票、期货、外汇甚至加密货币市场，并且适用于日线、周线及小时图等多种周期，但通常在震荡行情中效果有限。

我曾于 2017 年将 SuperTrend 指标代码转换至 Metastock 等多个平台，但在 TradingView 版本中，特别要感谢 everget - Alex Orekhov，他极大地启发了我，让我的指标在高亮、信号和警报方面表现得更好。感谢 Alex。