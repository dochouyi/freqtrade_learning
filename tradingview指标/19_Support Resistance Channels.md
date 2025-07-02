https://www.tradingview.com/v/Ej53t8Wv/

# Support Resistance Channels

![image-20250702105415359](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507021054432.png)



**该脚本工作原理**

- 脚本自动识别并保留枢轴点（Pivot Points）
- 每当发现新的枢轴点时，会清除旧的支撑/阻力（S/R）通道；
- 对于每一个枢轴点，脚本会在其动态宽度的通道内搜索所有枢轴点；
- 在创建S/R通道时，脚本会计算其强度；
- 随后按强度对所有S/R通道进行排序；
- 脚本仅显示最强的S/R通道，并在显示前检查其在列表中的原有位置，进行调整以提升可视性；
- 若某一S/R通道在最近一次价格变动中被突破，则脚本会发出警报，并在K线下方/上方标记形状；
- S/R通道的颜色会自动调整。

**可配置参数**

- **枢轴周期（Pivot Period）**
- **数据源（Source）**：可选用最高/最低价或收盘/开盘价
- **最大通道宽度百分比（Maximum Channel Width %）**：通道最大宽度占比，基于最近300根K线的最高/最低点计算
- **显示S/R通道数量（Number of S/R to show）**：显示最强S/R通道的数量
- **回溯周期（Loopback Period）**：计算S/R水平时，回溯检测枢轴点的周期
- **仅显示最近N根K线的S/R（Show S/R on last # Bars）**：仅在最近N根K线上显示S/R水平
- **起始日期（Start Date）**：从该日期开始计算枢轴点，设置该选项主要为优化视觉效果，详见下文说明
- 可自定义颜色与透明度
- 可启用/禁用S/R突破形状标记

**示例**

颜色可根据需求自定义：  
[![snapshot](https://www.tradingview.com/x/uNqxUEyT/)](https://www.tradingview.com/x/uNqxUEyT/)

下图“仅显示最近N根K线的S/R”设置为100：  
[![snapshot](https://www.tradingview.com/x/APqnQkbI/)](https://www.tradingview.com/x/APqnQkbI/)

有时由于历史S/R水平较多，视觉效果可能受影响。此时可在选项中设置“起始日期”，使脚本仅作用于可见区域（如最近292根K线）。下图第一张视觉效果较差（图形压缩），第二张设置“起始日期”后效果更佳。*若切换时间周期，请记得重新设置该参数* ：  
[![snapshot](https://www.tradingview.com/x/fQz4VIjp/)](https://www.tradingview.com/x/fQz4VIjp/)  
[![snapshot](https://www.tradingview.com/x/0ewP3QV9/)](https://www.tradingview.com/x/0ewP3QV9/)



































