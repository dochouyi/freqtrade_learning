https://cn.tradingview.com/v/L0AIiLvH/

# Pivot Point Supertrend

![image-20250701163115750](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011631821.png)

**Hello All,**

There are many types of SuperTrend around. Recently I thought about a Supertrend based on Pivot Points then I wrote **"Pivot Point SuperTrend"** script. It looks it has better performance on keeping you in the trend more.

The idea is behind this script is finding pivot point, calculating average of them and like in supertrend creating higher/lower bands by ATR. As you can see in the algorithm the script gives weigth to past pivot points, this is done for smoothing it a bit.


As I wrote above it may keep you in the trend more, lets see an example:
[![快照](https://www.tradingview.com/x/Ht07v5K2/)](https://www.tradingview.com/x/Ht07v5K2/)

As an option the script can show main center line and I realized that when you are in a position, this line can be used as early exit points. (maybe half of the position size)
[![快照](https://www.tradingview.com/x/9m2Q4Caf/)](https://www.tradingview.com/x/9m2Q4Caf/)

While using Pivot Points, I added support resistance lines by using Pivot Point, as an option the script can show S/R lines:
[![快照](https://www.tradingview.com/x/l5nmuf35/)](https://www.tradingview.com/x/l5nmuf35/)

And also it can show Pivot Points:
[![快照](https://www.tradingview.com/x/HnEY5aJD/)](https://www.tradingview.com/x/HnEY5aJD/)

When you changed Pivot Point Period you can see its reaction, in following example PP period is 4 (default value is 2). Smaller PP periods more sensitive trendlines.
[![快照](https://www.tradingview.com/x/hqRkAj9N/)](https://www.tradingview.com/x/hqRkAj9N/)

Alerts added for Buy/Sell entries and Trend Reversals. (when you set alerts use the option "*Once Per Bar Close*")



ENJOY!