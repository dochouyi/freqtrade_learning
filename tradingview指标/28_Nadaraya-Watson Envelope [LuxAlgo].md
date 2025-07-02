

https://www.tradingview.com/v/Iko0E2kL/

# Nadaraya-Watson Envelope [LuxAlgo]



![image-20250701160531033](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011605102.png)





该指标基于先前发布的 Nadaraya-Watson 平滑器进行扩展。此处我们构建了一个基于核平滑的包络线指标，并集成了价格与包络线极值交叉的预警功能。与 Nadaraya-Watson 估算器不同，本指标采用逆向思路。

请注意，默认情况下该指标可能存在重绘现象。用户可在设置中选择无重绘的平滑方法。三角形标记的设计旨在保证该指标在实时应用中的实用性。

**🔶 用法说明**

**🔹 无重绘模式**

[![snapshot](https://www.tradingview.com/x/eSy90JEz/)](https://www.tradingview.com/x/eSy90JEz/)

本工具可标示出价格的极端区间。其实现方式为先估算价格的潜在趋势，再计算其平均绝对偏差，最后将该偏差加/减于趋势估算值。

无重绘方法通过“端点 Nadaraya-Watson 估算器”来估算价格潜在趋势，结果与传统带状指标类似。

**🔹 重绘模式**

[![snapshot](https://www.tradingview.com/x/AsDVNltC/)](https://www.tradingview.com/x/AsDVNltC/)

重绘方法利用 Nadaraya-Watson 估算器估算价格的潜在趋势，包络线极值的构建方式与无重绘方法一致。

当价格穿越包络线极值时，通常可预期价格出现反转。价格与包络线极值的交叉处以三角形标记显示于图表上。

在实时应用中，三角形标记会在交叉发生时立即显示，并在首次出现的位置保持，即使后续包络线重算后该交叉已不再可见。

应广大用户需求，我们已集成了价格与包络线极值交叉的预警功能。然而，并不建议单独或仅用于实时应用中采用此方法。目前尚无数据表明该工具的表现优于传统带状/包络/通道类指标。

**🔶 参数设置**

- Bandwidth：控制包络线的平滑度，数值越大，结果越平滑。
- Mult：控制包络线的宽度。
- Source：指标的数据输入源。
- Repainting Smoothing：选择指标计算时采用重绘或无重绘平滑方法。



























































































