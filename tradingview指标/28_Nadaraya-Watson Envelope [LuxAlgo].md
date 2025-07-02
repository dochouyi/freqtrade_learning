

https://www.tradingview.com/v/Iko0E2kL/

# Nadaraya-Watson Envelope [LuxAlgo]



![image-20250701160531033](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011605102.png)





This indicator builds upon the previously posted Nadaraya-Watson smoothers. Here we have created an envelope indicator based on Kernel Smoothing with integrated alerts from crosses between the price and envelope extremities. Unlike the Nadaraya-Watson estimator, this indicator follows a contrarian methodology.

Please note that by default this indicator can be subject to repainting. Users can use a non-repainting smoothing method available from the settings. The triangle labels are designed so that the indicator remains useful in real-time applications.

**🔶 USAGE**

**🔹 Non Repainting**

[![snapshot](https://www.tradingview.com/x/eSy90JEz/)](https://www.tradingview.com/x/eSy90JEz/)

This tool can outline extremes made by the prices. This is achieved by estimating the underlying trend in the price, then calculating the mean absolute deviations from it, the obtained result is added/subtracted to the estimated underlying trend.

The non-repainting method estimates the underlying trend in price using an "endpoint Nadaraya-Watson estimator", and would return similar results to more classical band indicators.

**🔹 Repainting**

[![snapshot](https://www.tradingview.com/x/AsDVNltC/)](https://www.tradingview.com/x/AsDVNltC/)

The repainting method makes use of the Nadaraya-Watson estimator to estimate the underlying trend in the price. The construction of the band extremities is the same as in the non-repainting method.

We can expect the price to reverse when crossing one of the envelope extremities. Crosses between the price and the envelopes extremities are indicated with triangles on the chart.

For real-time applications, triangles are always displayed when a cross occurs and remain displayed at the location it first appeared even if the cross is no longer visible after a recalculation of the envelope.

By popular demand, we have integrated alerts for this indicator from the crosses between the price and the envelope extremities. However, we do not recommend this precise method to be used alone or for solely real-time applications. We do not have data supporting the performance of this tool over more classical bands/envelope/channels indicators.

**🔶 SETTINGS**



- Bandwidth: Controls the degree of smoothness of the envelopes, with higher values returning smoother results.
- Mult: Controls the envelope width.
- Source: Input source of the indicator.
- Repainting Smoothing: Determine if a repainting or non-repainting method should be used for the calculation of the indicator.



























































































