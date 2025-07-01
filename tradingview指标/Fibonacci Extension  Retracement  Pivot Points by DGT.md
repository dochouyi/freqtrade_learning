https://www.tradingview.com/script/FWYQ4vTk-Fibonacci-Extension-Retracement-Pivot-Points-by-DGT/

# Fibonacci Extension / Retracement / Pivot Points by DGT

![image-20250701162639011](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011626083.png)





**Fɪʙᴏɴᴀᴄᴄɪ Exᴛᴇɴᴛɪᴏɴ / Rᴇᴛʀᴀᴄᴍᴇɴᴛ / Pɪᴠᴏᴛ Pᴏɪɴᴛꜱ**
This study combines various Fibonacci concepts into one, and some basic volume and volatility indications

█  **Pɪᴠᴏᴛ Pᴏɪɴᴛꜱ** — is a technical indicator that is used to determine the levels at which price may face support or resistance. The Pivot Points indicator consists of a pivot point (PP) level and several support (S) and resistance (R) levels. PP, resistance and support values are calculated in different ways, depending on the type of the indicator, this study implements Fibonacci Pivot Points

The indicator resolution is set by the input of the Pivot Points TF (Timeframe). If the Pivot Points TF is set to AUTO (the default value), then the increased resolution is determined by the following algorithm:
   for intraday resolutions up to and including 5 min, 4HOURS (4H) is used
   for intraday resolutions more than 5 min and up to and including 45 min, DAY (1D) is used
   for intraday resolutions more than 45 min and up to and including 4 hour, WEEK (1W) is used
   for daily resolutions MONTH is used (1M)
   for weekly resolutions, 3-MONTH (3M) is used
   for monthly resolutions, 12-MONTH (12M) is used

If the Pivot Points TF is set to User Defined, users may choose any higher timeframe of their preference

[![snapshot](https://www.tradingview.com/x/a2p4fYgg/)](https://www.tradingview.com/x/a2p4fYgg/)



█  **Fɪʙ Rᴇᴛʀᴀᴄᴇᴍᴇɴᴛ** — Fibonacci retracements is a popular instrument used by technical analysts to determine support and resistance areas. In technical analysis, this tool is created by taking two extreme points (usually a peak and a trough) on the chart and dividing the vertical distance by the key Fibonacci coefficients equal to 23.6%, 38.2%, 50%, 61.8%, and 100%. This study implements an automated method of identifying the pivot lows/highs and automatically draws horizontal lines that are used to determine possible support and resistance levels
[![snapshot](https://www.tradingview.com/x/uj9tIsJr/)](https://www.tradingview.com/x/uj9tIsJr/)


█  **Fɪʙᴏɴᴀᴄᴄɪ Exᴛᴇɴꜱɪᴏɴꜱ** — Fibonacci extensions are a tool that traders can use to establish profit targets or estimate how far a price may travel AFTER a retracement/pullback is finished. Extension levels are also possible areas where the price may reverse. This study implements an automated method of identifying the pivot lows/highs and automatically draws horizontal lines that are used to determine possible support and resistance levels.

***IMPORTANT NOTE:\*** Fibonacci extensions option may require to do further adjustment of the study parameters for proper usage. Extensions are aimed to be used when a trend is present and they aim to measure how far a price may travel AFTER a retracement/pullback. I will strongly suggest users of this study to check the education post for further details, [where to use extensions and where to use retracements](https://www.tradingview.com/chart/BTCUSDT/jKRJoimq-fibonacci-extensions-retracements-how-to-and-where-to-apply/)

[![snapshot](https://www.tradingview.com/x/iKlSJrzO/)](https://www.tradingview.com/x/iKlSJrzO/)

[![snapshot](https://www.tradingview.com/x/DYZi4lY7/)](https://www.tradingview.com/x/DYZi4lY7/)


Important input options for both Fibonacci Extensions and Retracements
Deviation, is a multiplier that affects how much the price should deviate from the previous pivot in order for the bar to become a new pivot. Increasing its value is one way to get higher timeframe Fib Retracement Levels
Depth, affects the minimum number of bars that will be taken into account when building


█  **Volume / Volatility Add-Ons**
  **High Volatile Bar Indication**

  **Volume Spike Bar Indication**

  **Volume Weighted Colored Bars**

[![snapshot](https://www.tradingview.com/x/mE4VF0pn/)](https://www.tradingview.com/x/mE4VF0pn/)

This study benefits from build-in auto fib retracement tv study and modifications applied to get extentions and also to fit this combo

**Disclaimer:**
Trading success is all about following your trading strategy and the indicators should fit within your trading strategy, and not to be traded upon solely

The script is for informational and educational purposes only. Use of the script does not constitute professional and/or financial advice. You alone have the sole responsibility of evaluating the script output and risks associated with the use of the script. In exchange for using the script, you agree not to hold dgtrd TradingView user liable for any possible claim for damages arising from any decision you make based on use of the script