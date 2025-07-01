https://www.tradingview.com/script/n8AGnIZd-Divergence-for-Many-Indicators-v4/



# Divergence for Many Indicators v4

![image-20250701155844917](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011558978.png)



**Hello Traders,**


Here is my new year gift for the community, **Digergence for Many Indicators v4**. I tried to make it modular and readable as much as I can. Thanks to Pine Team for improving Pine Platform all the time!

**How it works?**
\- On each candle it checks divergences between current and any of last 16 Pivot Points for the indicators.
\- it search divergence on choisen indicators => **RSI , MACD , MACD Histogram, Stochastic , CCI , Momentum, OBV, VWMACD, CMF** and *any External Indicator*!
\- it checks following divergences for 16 pivot points that is in last 100 bars for each Indicator.
--> Regular Positive Digergences
--> Regular Negative Digergences
--> Hidden Positive Digergences
--> Hidden Negative Digergences
\- for positive divergences first it checks if closing price is higher than last closing price and indicator value is higher than perious value, then start searching divergence
\- for negative divergences first it checks if closing price is lower than last closing price and indicator value is lower than perious value, then start searching divergence


**Some Options:**

Pivot Period: you set Pivot Period as you wish. you can see Pivot Points using "Show Pivot Points" option
**Source for Pivot Points:** you can use Close or High/Low as source
**Divergence Type:** you can choose Divergence type to be shown => *"Regular", "Hidden", "Regular/Hidden"*
**Show Indicator Names:** you have different options to show indicator names => *"Full", "First Letter", "Don't Show"*
**Show Divergence Number:** option to see number of indicators which has Divergence
**Show Only Last Divergence**: if you enable this option then it shows only last Positive and Negative Divergences
you can include any **External Indicator** to see if there is divergence
\- enable *"Check External Indicator"*
\- and then choose External indicator name in the list, *"External Indicator"*
\- External indicator name is shown as **Extrn**
\- *related external indicator must be added before enabling this option*

**Coloring, line width and line style options for different type of divergences.**

**Following Alerts added:**
*- Positive Regular Divergence Detected
\- Negative Regular Divergence Detected
\- Positive Hidden Divergence Detected
\- Negative Hidden Divergence Detected
*

**Now lets see some examples:**

Hidden Divergences:

![image-20250701155904649](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559710.png)



Regular and Hidden Divergences together:

![image-20250701155927807](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559871.png)

Showing first letters of indicators:

![image-20250701155941951](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559008.png)



You can see only the number of indicators which has divergence:

![image-20250701155956103](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559160.png)





You can see only divergence lines without indicators names and numbers:
[![snapshot](https://www.tradingview.com/x/ZZW0yFJn/)](https://www.tradingview.com/x/ZZW0yFJn/)

option to used different label/line/text colors:
[![snapshot](https://www.tradingview.com/x/VQYZsfGN/)](https://www.tradingview.com/x/VQYZsfGN/)

You have option to see only last divergences:
[![snapshot](https://www.tradingview.com/x/MIk3VAMI/)](https://www.tradingview.com/x/MIk3VAMI/)

You can change Pivot Period, in following example Pivot Period = 15:
[![snapshot](https://www.tradingview.com/x/LdH2JWjk/)](https://www.tradingview.com/x/LdH2JWjk/)

You can use Close or High/Low as Source for Divergence
[![snapshot](https://www.tradingview.com/x/BKiVm72U/)](https://www.tradingview.com/x/BKiVm72U/)

You can include external indicators and get divergences on it:
[![snapshot](https://www.tradingview.com/x/he5jokt3/)](https://www.tradingview.com/x/he5jokt3/)

**Wish you all a happy new year!**

**Enjoy!**





























































