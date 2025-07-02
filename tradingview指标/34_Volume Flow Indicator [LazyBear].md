https://www.tradingview.com/v/MhlDpfdS/

# Volume Flow Indicator [LazyBear]

![image-20250702110125014](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507021101092.png)


## VFI（成交量流向指标）简介

**VFI**（Volume Flow Indicator）由Markos Katsanos提出，是基于经典OBV（On Balance Volume，能量潮指标）发展而来的成交量类指标，但进行了三项重要改进：

### 三大改进

1. **指标数值具备明确意义**  
   - 与OBV不同，VFI的数值可直接解读：  
     - 指标为正代表多头（看涨）；  
     - 指标为负代表空头（看跌）。
2. **基于中间价计算**  
   - 计算时采用当日中间价（typical price，即 \[(最高价 + 最低价 + 收盘价)/3\]），而非单一收盘价。
3. **波动性与极端量过滤**  
   - 设置波动性阈值，排除微小价格变动；  
   - 通过另一个阈值剔除异常巨量，提升信号质量。

### 指标解读

- **零轴判定**：  
  - VFI高于零表示市场处于多头状态，零线交叉常作为买入信号触发点。
- **背离信号**：  
  - 与所有资金流指标类似，VFI与价格的背离是最强烈的交易信号之一。

### 参数与优化

- **信号EMA**：  
  - 脚本支持绘制信号EMA，所有参数均可自定义调整。
- **权重系数建议**：  
  - Markos建议：日内交易用0.2系数，超短线（intra-day）用0.1。

### 更多信息

- 详见原作者页面：[precisiontradingsystems.com/VOLUME_FLOW.htm](http://www.precisiontradingsystems.com/VOLUME_FLOW.htm)

---

**总结：**  
VFI通过三项创新改进，让成交量分析更具方向性和可操作性。其零轴突破与背离信号对趋势判断和交易决策具有重要参考价值。所有参数可调，适用于不同周期和风格的量价分析。