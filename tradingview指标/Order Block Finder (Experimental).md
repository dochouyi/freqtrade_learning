https://www.tradingview.com/v/R8g2YHdg/

# Order Block Finder (Experimental)

![image-20250701161022507](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011610573.png)

The purpose of this experimental Indicator is to help identifying Institutional Order Blocks.

Often these Order Blocks can be observed at the beginning of a strong move, but there is a significant probability that these price levels will be revisited at a later point in time again. Therefore these are interesting levels to place limit orders (Buy Orders for Bullish OB / Sell Orders for Bearish OB).

A Bullish Order block is defined as the last down candle before a sequence of up candles. (Relevant price range "Open" to "Low" is marked)
A Bearish Order Block is defined as the last up candle before a sequence of down candles. (Relevant price range "Open" to "High" is marked)

In the settings the number of required sequential candles can be adjusted.
Furthermore a %-threshold can be entered. It defines which minimum %-change the sequential move needs to achieve in order to identify a relevant Order Block. If this is used, it makes sense to adjust it to the timeframe which is analyzed as of course higher timeframes usually produce bigger moves.

Channels for the last Bullish/Bearish Block can be shown/hidden.

In addition to the upper/lower limits of each Order Block, also the equlibrium (average value) is marked as this is an interesting area for price interaction.

Please note that you can optionally display a "Docu"-Label which shows some information about the indicator as a tooltip.

Remark:
As the identification of a relevant Order Block is only possible after the required number of subsequent candles has closed, this indicator "repaints" by definition. But I do not see this as an issue as the relevancy of the Order Blocks and the interaction of price with these levels usually only happens longer in the future anyway.

Sep 17, 2020

Release Notes

Update:

Received the request from @AtotheO to give the option to mark the full range "Low" to "High" (including both wicks) for each identified OB.

The underlying reason why I only used Open-Low for Bullish OBs and Open-High for Bearish OBs was the thought, that Institutional Investors are using these candles for their initial entries. So the assumption is that they are behaving "more smart" than the general market and tend to buy lower/sell higher that the average and therefore most probably have a more favourable entry price than the average. Therefore I left out the "unfavourable" wicks.

But I agree with the opinion that this should be selectable by the user of the indicator and here is the update:

New input field allows to select "Use whole range [High/Low] for OB marking". By default it is de-selected.

Enjoy.















































