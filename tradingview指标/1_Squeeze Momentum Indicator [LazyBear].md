https://www.tradingview.com/v/nqQ1DT5a/

# Squeeze动量指标 [LazyBear]

![image-20250701145512638](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507011455725.png)



1. **指标来源**：约翰·卡特的TTM挤压波动性指标，详见其书籍《交易的艺术》第11章。

2. **黑交叉**：在中线上显示，表示市场进入挤压状态（布林带在凯尔特纳通道内），意味着低波动性，市场准备出现爆炸性动向。

3. **灰色交叉**：在中线上显示，表示挤压释放。

4. **入场时机**：建议等待第一次灰色交叉后，根据动量方向入场（如动量高于零则做多）。

5. **出场策略**：动量变化时退出头寸，变化通过颜色变化表示。

6. **附加工具**：建议使用其他指标（如ADX/WaveTrend）来捕捉良好的入场点。

7. **方法差异**：卡特使用简单的动量指标，而文中使用基于线性回归的直方图绘制方法。




```angular2html
下面是对你提供的 Pine Script 代码逐行详细注释：

```pine
// @author LazyBear 
// List of all my indicators: https://www.tradingview.com/v/4IneGo8h/
//
study(shorttitle = "SQZMOM_LB", title="Squeeze Momentum Indicator [LazyBear]", overlay=false)
// 定义指标基本信息，shorttitle为简写，title为完整名，overlay=false表示不画在K线图上

length = input(20, title="BB Length")
// 设置布林带（BB）周期为20，可调

mult = input(2.0,title="BB MultFactor")
// 设置布林带标准差倍数为2.0，可调

lengthKC=input(20, title="KC Length")
// 设置肯特纳通道（KC）周期为20，可调

multKC = input(1.5, title="KC MultFactor")
// 设置肯特纳通道倍数为1.5，可调

useTrueRange = input(true, title="Use TrueRange (KC)", type=bool)
// 是否在KC计算中使用True Range，默认为true

// Calculate BB
source = close
// 数据源为收盘价

basis = sma(source, length)
// 计算BB中线（简单移动平均）

dev = multKC * stdev(source, length)
// 计算BB标准差带宽（标准差*倍数）

upperBB = basis + dev
// 计算BB上轨

lowerBB = basis - dev
// 计算BB下轨

// Calculate KC
ma = sma(source, lengthKC)
// KC中线（简单移动平均）

range = useTrueRange ? tr : (high - low)
// 如果useTrueRange为true，range取真实波幅，否则为最高-最低

rangema = sma(range, lengthKC)
// 计算range的移动平均

upperKC = ma + rangema * multKC
// KC上轨

lowerKC = ma - rangema * multKC
// KC下轨

sqzOn  = (lowerBB > lowerKC) and (upperBB < upperKC)
// Squeeze信号开启：BB完全在KC内

sqzOff = (lowerBB < lowerKC) and (upperBB > upperKC)
// Squeeze信号关闭：BB完全在KC外

noSqz  = (sqzOn == false) and (sqzOff == false)
// 没有Squeeze信号

val = linreg(
// 计算动量柱值：用线性回归拟合当前价和高低区间的偏离
    source  -  avg(
        avg(highest(high, lengthKC), lowest(low, lengthKC)),
        sma(close,lengthKC)
    ), 
    lengthKC, 0
)

bcolor = iff( val > 0, 
            iff( val > nz(val[1]), lime, green),
            iff( val < nz(val[1]), red, maroon))
// 根据动量柱的值和变化，决定柱子的颜色：上涨变亮绿，下跌深绿；下跌变亮红，下跌深红

scolor = noSqz ? blue : sqzOn ? black : gray 
// 根据Squeeze状态决定0轴颜色：无Squeeze为蓝，有Squeeze为黑，否则为灰

plot(val, color=bcolor, style=histogram, linewidth=4)
// 画动量柱，颜色随bcolor，宽度4

plot(0, color=scolor, style=cross, linewidth=2)
// 画0轴，颜色随Squeeze状态变化，宽度2
```

---

### 总结说明

- 该脚本为**Squeeze Momentum Indicator**，结合了布林带（BB）和肯特纳通道（KC）的特性，用以判断市场是否处于“挤压”状态（即波动率极低，往往预示着即将爆发行情）。
- **动量柱**通过线性回归拟合价格与区间均值的偏离，显示市场动能强弱，并用不同颜色区分趋势变化。
- **0轴颜色**显示当前市场是否处于Squeeze状态，便于视觉识别。

如果需要更详细的公式推导或应用说明，也可以继续问我！
```


