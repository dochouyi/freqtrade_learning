https://www.tradingview.com/v/IYL88A1N/

# Trendlines with Breaks [LuxAlgo]

![image-20250702104912323](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507021049403.png)



趋势线断点指标基于枢轴点绘制趋势线，并高亮显示突破点。用户可自主调节趋势线的陡峭程度及其斜率的计算方法。

趋势线突破实时发生，不会出现回溯描绘（backpainting）。但趋势线本身可能会重绘，除非用户在设置中禁用该功能。

本指标集成了趋势线突破的实时提醒功能。

**🔶 用法**

[![snapshot](https://www.tradingview.com/x/zH8lZTho/)](https://www.tradingview.com/x/zH8lZTho/)

该指标适用于任何有效的趋势线方法，用户可据此识别突破，从而推测未来价格走势。

斜率的计算方法对趋势线行为影响显著。默认采用平均真实波幅（ATR）计算，能够使各条趋势线斜率更为一致。其他方法可能生成斜率差异较大的趋势线。

*Stdev* 使用标准差进行斜率计算，而 *Linreg* 则采用线性回归的斜率。

[![snapshot](https://www.tradingview.com/x/wuwoZqW7/)](https://www.tradingview.com/x/wuwoZqW7/)

上图展示了以“Stdev”为斜率计算方法的指标效果。下图则采用了“Linreg”方法。

[![snapshot](https://www.tradingview.com/x/PwugXvQ7/)](https://www.tradingview.com/x/PwugXvQ7/)

默认情况下，趋势线会进行回溯描绘，因此会向历史*length*根K线处偏移。若禁用回溯描绘，则趋势线不会发生偏移。

[![snapshot](https://www.tradingview.com/x/Bc3sPeZq/)](https://www.tradingview.com/x/Bc3sPeZq/)

**🔶 设置**

- Length：枢轴点周期
- Slope：斜率陡峭度，值大于1时斜率更陡。斜率为0等同于获取水平线。
- Slope Calculation Method：斜率的计算方式。
- Backpaint：是否进行回溯描绘，即趋势线是否向历史偏移。

































