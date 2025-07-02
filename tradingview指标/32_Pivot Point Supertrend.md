https://cn.tradingview.com/v/L0AIiLvH/

# Pivot Point Supertrend

![image-20250701163115750](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011631821.png)

## Pivot Point SuperTrend 指标说明

大家好，

市面上有许多类型的SuperTrend（超级趋势）指标。近期我思考了一个基于枢轴点（Pivot Point）的SuperTrend，并编写了**“Pivot Point SuperTrend”**脚本。实测发现，该指标在趋势跟随方面表现更优，能更有效地让你持有趋势头寸。

### 核心思想

本脚本的核心思想是：  
- 首先识别枢轴点（Pivot Point），并计算其均值，用于作为趋势的参考中心线。
- 类似传统SuperTrend，利用ATR（平均真实波幅）构建上下波动带（高/低带）。
- 算法中对历史枢轴点赋予权重，实现平滑处理，减少噪音。

### 指标特性与用法

- **趋势跟随能力更强**：如示例图所示，Pivot Point SuperTrend能更好地让你跟随趋势，避免频繁出场。
  - ![趋势示例](https://www.tradingview.com/x/Ht07v5K2/)

- **中心线用作提前止盈**：脚本可选显示主中心线。当持仓时，可将此线作为提前部分止盈的参考点。
  - ![中心线示例](https://www.tradingview.com/x/9m2Q4Caf/)

- **支撑/阻力线显示**：利用枢轴点可自动绘制支撑/阻力线，作为辅助判断。
  - ![支撑阻力示例](https://www.tradingview.com/x/l5nmuf35/)

- **枢轴点显示**：可选直接在图表上标注各个枢轴点。
  - ![枢轴点示例](https://www.tradingview.com/x/HnEY5aJD/)

- **参数灵活调整**：可调整枢轴点周期（如PP period=4，默认2），周期越小，趋势线越敏感，适合不同交易风格。
  - ![周期调整示例](https://www.tradingview.com/x/hqRkAj9N/)

### 警报功能

- 已内置买入/卖出及趋势反转的警报功能。
- 设置警报时建议选择“每根K线收盘时触发（Once Per Bar Close）”。

---

**总结：**  
Pivot Point SuperTrend结合了枢轴点和ATR的优点，通过对历史枢轴点加权平均，实现趋势线平滑且跟随性强。可视化中心线、支撑阻力以及灵活参数设置，使其在趋势跟随和交易管理中具有较高实用价值。
