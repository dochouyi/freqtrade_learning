https://www.tradingview.com/script/n8AGnIZd-Divergence-for-Many-Indicators-v4/



# Divergence for Many Indicators v4

![image-20250701155844917](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011558978.png)


**多指标背离检测 v4（Digergence for Many Indicators v4）**

**工作原理说明：**  
\- 在每根K线时，脚本会检测当前K线与过去16个任意枢轴点之间的背离情况。  
\- 支持检测的指标包括：**RSI、MACD、MACD柱、随机指标（Stochastic）、CCI、动量（Momentum）、OBV、VWMACD、CMF** 及*任意外部指标*！  
\- 针对每个指标，在最近100根K线内的16个枢轴点上，检测以下背离类型：  
 → 常规正背离  
 → 常规负背离  
 → 隐性正背离  
 → 隐性负背离  
\- 对于正背离，首先判断收盘价是否高于上一个收盘价且指标值高于前值，若满足则开始检测背离。  
\- 对于负背离，首先判断收盘价是否低于上一个收盘价且指标值低于前值，若满足则开始检测背离。

**部分选项说明：**

- 枢轴周期（Pivot Period）：可自定义设置。勾选“显示枢轴点”可查看枢轴点分布。
- **枢轴点来源（Source for Pivot Points）：** 可选择收盘价或最高/最低价。
- **背离类型（Divergence Type）：** 可选择显示的背离类型——*"常规"、"隐性"、"常规/隐性"*。
- **显示指标名称：** 可选择不同显示方式——*"全称"、"首字母"、"不显示"*。
- **显示背离指标数量：** 可显示出现背离的指标数量。
- **仅显示最近一次背离：** 勾选后，仅显示最近一次正背离和负背离。
- 可引入**外部指标**并检测其背离：
  - 启用 *“检测外部指标”*；
  - 在列表中选择外部指标名称 *“External Indicator”*；
  - 外部指标名称显示为 **Extrn**；
  - *需先添加相关外部指标后方可启用此项*。

- 支持为不同类型背离自定义颜色、线宽及线型。

**已添加的预警类型：**  
*- 检测到常规正背离  
\- 检测到常规负背离  
\- 检测到隐性正背离  
\- 检测到隐性负背离  
*

**以下为部分示例：**

隐性背离展示：

![image-20250701155904649](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559710.png)

常规与隐性背离同时显示：

![image-20250701155927807](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559871.png)

仅显示指标首字母：

![image-20250701155941951](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559008.png)

仅显示出现背离的指标数量：

![image-20250701155956103](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011559160.png)

仅显示背离线，不显示指标名称和数量：  
[![snapshot](https://www.tradingview.com/x/ZZW0yFJn/)](https://www.tradingview.com/x/ZZW0yFJn/)

可自定义标签/线条/文字颜色：  
[![snapshot](https://www.tradingview.com/x/VQYZsfGN/)](https://www.tradingview.com/x/VQYZsfGN/)

可仅显示最近一次背离：  
[![snapshot](https://www.tradingview.com/x/MIk3VAMI/)](https://www.tradingview.com/x/MIk3VAMI/)

可调整枢轴周期，以下示例枢轴周期=15：  
[![snapshot](https://www.tradingview.com/x/LdH2JWjk/)](https://www.tradingview.com/x/LdH2JWjk/)

可选择收盘价或高/低价作为背离检测来源：  
[![snapshot](https://www.tradingview.com/x/BKiVm72U/)](https://www.tradingview.com/x/BKiVm72U/)

可引入外部指标并检测其背离：  
[![snapshot](https://www.tradingview.com/x/he5jokt3/)](https://www.tradingview.com/x/he5jokt3/)




























































