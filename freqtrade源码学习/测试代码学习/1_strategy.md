

![image-20250704153322118](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041533164.png)

---

![image-20250704153621684](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041536726.png)

![image-20250704153608164](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041536221.png)



![image-20250704153830406](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041538451.png)



![image-20250704154002057](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041540106.png)





---

![image-20250704154439882](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041544925.png)



![image-20250704154454445](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041544489.png)



![image-20250704154716965](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507041547009.png)



---

![image-20250707144338885](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071443976.png)



![image-20250707163232646](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071632685.png)

---



![image-20250707163402745](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071634787.png)

```
strategy.custom_roi = MagicMock(side_effect=custom_roi)
```

- 使用 `unittest.mock.MagicMock` 创建一个模拟对象，并将其 `side_effect` 设置为 `custom_roi` 函数。
- 这样，每当调用 `strategy.custom_roi(...)` 时，实际会执行 `custom_roi` 函数的逻辑。
- 常用于单元测试，模拟和验证函数调用及其返回值。

---

![image-20250707164625762](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071646813.png)

![image-20250707164721603](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071647654.png)

![image-20250707164800148](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071648187.png)



![image-20250707165000470](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071650513.png)

---

## 1. 日志等级设置

```python
caplog.set_level(logging.DEBUG)
```
- 这行代码设置日志捕获器（`caplog`，一般用于pytest的日志捕获fixture）的日志等级为 `DEBUG`。
- 这样可以捕获到调试级别及以上的所有日志，方便后续调试和测试中查看详细日志输出。

---

## 2. 创建 MagicMock 对象

```python
ind_mock = MagicMock(side_effect=lambda x, meta: x)
entry_mock = MagicMock(side_effect=lambda x, meta: x)
exit_mock = MagicMock(side_effect=lambda x, meta: x)
```
- 分别创建了三个 `MagicMock` 模拟对象，分别用于指标、入场和出场建议。
- 这三个模拟对象的 `side_effect` 都是一个简单的 lambda 函数：`lambda x, meta: x`，即无论传什么参数，都会返回第一个参数 `x`。
- 这样设置方便后续验证函数是否被调用，以及调用了多少次。

---

## 3. mocker.patch.multiple

```python
mocker.patch.multiple(
    "freqtrade.strategy.interface.IStrategy",
    advise_indicators=ind_mock,
    advise_entry=entry_mock,
    advise_exit=exit_mock,
)
```
- 使用 `pytest-mock` 的 `mocker.patch.multiple` 方法，对 `freqtrade.strategy.interface.IStrategy` 这个类的三个方法进行打桩（mock）。
- 分别将 `advise_indicators`, `advise_entry`, `advise_exit` 替换为上面定义的 mock 对象。
- 这样，后续对这三个方法的调用都会被记录到 mock 对象中，便于测试和断言。

---

## 4. 实例化策略并分析行情

```python
strategy = StrategyTestV3({})
strategy.analyze_ticker(ohlcv_history, {"pair": "ETH/BTC"})
```
- 创建了一个 `StrategyTestV3` 实例（传入空字典作为参数）。
- 调用 `strategy.analyze_ticker` 方法，对 `ohlcv_history`（K线历史数据）和指定交易对（`"ETH/BTC"`）进行分析。
- 在分析过程中，`advise_indicators`、`advise_entry` 和 `advise_exit` 方法会被调用，但由于已经被 mock，所以实际调用的是 mock 对象。

---

## 5. 断言调用次数

```python
assert ind_mock.call_count == 1
assert entry_mock.call_count == 1
assert entry_mock.call_count == 1
```
- 断言 `ind_mock` 被调用了一次。
- 断言 `entry_mock` 被调用了一次。
- 注意：`entry_mock.call_count == 1` 写了两次，应该有一个是 `exit_mock.call_count == 1`，这里可能是笔误。

正确应该是：

```python
assert ind_mock.call_count == 1
assert entry_mock.call_count == 1
assert exit_mock.call_count == 1
```

---

## 6. 总结

- 此代码片段用于测试策略分析流程中，指标建议、入场建议、出场建议是否各自被正确调用了一次。
- 通过 mock 和断言，确保策略的分析流程按照预期执行。
- 适用于单元测试环境，常见于基于 pytest 的自动化测试脚本。

---

如果你需要更具体的解释，比如每个 mock 的作用、如何扩展测试等，可以继续提问！

---

![image-20250707170222519](https://pkuxiaohou.oss-cn-beijing.aliyuncs.com/img/202507071702570.png)

策略可以设置某一个币的锁定与否

























































































































