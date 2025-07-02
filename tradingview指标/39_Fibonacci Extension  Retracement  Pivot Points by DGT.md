https://www.tradingview.com/script/FWYQ4vTk-Fibonacci-Extension-Retracement-Pivot-Points-by-DGT/

# Fibonacci Extension / Retracement / Pivot Points by DGT

![image-20250701162639011](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011626083.png)


**Fɪʙᴏɴᴀᴄᴄɪ 扩展 / 回撤 / 枢轴点**
本研究将多种斐波那契概念合并于一体，并引入了部分基础的成交量与波动性指示。

█  **枢轴点（Pivot Points）** —— 枢轴点是一种技术指标，用于确定价格可能遇到支撑或阻力的位置。枢轴点指标包含一个枢轴点（PP）水平及若干支撑（S）和阻力（R）水平。PP、阻力和支撑值的计算方式因指标类型而异，本研究实现了斐波那契枢轴点。

指标分辨率由枢轴点时间框架（TF）输入设置。若枢轴点TF设为AUTO（默认值），则更高分辨率按如下算法确定：
- 对于5分钟及以内的日内分辨率，采用4小时（4H）
- 对于大于5分钟且不超过45分钟的日内分辨率，采用天（1D）
- 对于大于45分钟且不超过4小时的日内分辨率，采用周（1W）
- 对于日线分辨率，采用月（1M）
- 对于周线分辨率，采用3个月（3M）
- 对于月线分辨率，采用12个月（12M）

若枢轴点TF设为用户自定义，用户可选择任意更高时间框架。

[![snapshot](https://www.tradingview.com/x/a2p4fYgg/)](https://www.tradingview.com/x/a2p4fYgg/)

█  **斐波那契回撤（Fib Retracement）** —— 斐波那契回撤是技术分析师常用来判断支撑和阻力区域的工具。在技术分析中，该工具通过选取图表上的两个极端点（通常为高点和低点），并以23.6%、38.2%、50%、61.8%、100%等关键斐波那契系数划分其垂直距离。本研究实现了自动识别枢轴高低点的方法，并自动绘制用于判断潜在支撑和阻力水平的水平线。
[![snapshot](https://www.tradingview.com/x/uj9tIsJr/)](https://www.tradingview.com/x/uj9tIsJr/)

█  **斐波那契扩展（Fibonacci Extensions）** —— 斐波那契扩展是交易者用于设定盈利目标或估算价格在回撤/回调结束后可能运行距离的工具。扩展水平也可能成为价格反转的区域。本研究实现了自动识别枢轴高低点的方法，并自动绘制用于判断潜在支撑和阻力水平的水平线。

***重要说明：*** 斐波那契扩展选项可能需要进一步调整参数以便正确使用。扩展主要用于趋势存在时，目的是衡量价格在回撤/回调之后可能的运行距离。强烈建议用户查阅相关教育文章，了解[扩展与回撤的适用场景](https://www.tradingview.com/chart/BTCUSDT/jKRJoimq-fibonacci-extensions-retracements-how-to-and-where-to-apply/)。

[![snapshot](https://www.tradingview.com/x/iKlSJrzO/)](https://www.tradingview.com/x/iKlSJrzO/)

[![snapshot](https://www.tradingview.com/x/DYZi4lY7/)](https://www.tradingview.com/x/DYZi4lY7/)

斐波那契扩展与回撤的重要参数选项：
- 偏差（Deviation）：为一乘数，决定价格需相较前一枢轴偏离多少，当前K线才被视为新枢轴。提高该值可获得更高时间框架的回撤水平。
- 深度（Depth）：影响在构建时所考虑的最小K线数量。

█  **成交量 / 波动性附加功能**
- **高波动K线指示**
- **成交量激增K线指示**
- **成交量加权彩色K线**

[![snapshot](https://www.tradingview.com/x/mE4VF0pn/)](https://www.tradingview.com/x/mE4VF0pn/)

本研究基于内置自动斐波那契回撤脚本，进行了扩展和适配以实现上述组合。