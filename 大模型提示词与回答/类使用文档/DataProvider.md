`DataProvider` 是 Freqtrade 中负责数据管理的核心类，位于 [1](#0-0) 。

## DataProvider 类 SDK 使用说明

### 概述

`DataProvider` 是 Freqtrade 的统一数据访问接口，为策略和其他组件提供历史数据、实时市场数据、订单簿数据等各种数据源的访问能力 [2](#0-1) 。

### 初始化

DataProvider 在 FreqtradeBot 初始化时自动创建并注入到策略中： [3](#0-2) 

### 核心方法

#### 1. 获取交易对数据

**`get_pair_dataframe(pair, timeframe)`** - 获取指定交易对的 OHLCV 数据 [4](#0-3) 

```python
# 获取历史/实时蜡烛数据
inf_pair, inf_timeframe = self.informative_pairs()[0]
informative = self.dp.get_pair_dataframe(pair=inf_pair, timeframe=inf_timeframe)
```

#### 2. 获取已分析数据

**`get_analyzed_dataframe(pair, timeframe)`** - 获取经过策略分析处理的数据框 [5](#0-4) 

```python
# 获取当前数据框
dataframe, last_updated = self.dp.get_analyzed_dataframe(pair=metadata['pair'], timeframe=self.timeframe)
```

#### 3. 市场数据访问

**`orderbook(pair, maximum)`** - 获取订单簿数据 [6](#0-5) 

```python
if self.dp.runmode.value in ('live', 'dry_run'):
    ob = self.dp.orderbook(metadata['pair'], 1)
    dataframe['best_bid'] = ob['bids'][0][0]
    dataframe['best_ask'] = ob['asks'][0][0]
```

**`ticker(pair)`** - 获取当前价格数据 [7](#0-6) 

```python
if self.dp.runmode.value in ('live', 'dry_run'):
    ticker = self.dp.ticker(metadata['pair'])
    dataframe['last_price'] = ticker['last']
    dataframe['volume24h'] = ticker['quoteVolume']
```

#### 4. 白名单管理

**`current_whitelist()`** - 获取当前白名单 [8](#0-7) [9](#0-8) 

#### 5. 外部数据生产者

**`get_producer_df(pair, timeframe, candle_type, producer_name)`** - 获取外部数据源的数据 [10](#0-9) [11](#0-10) 

#### 6. 消息发送

**`send_msg(message, always_send=False)`** - 发送自定义通知消息 [12](#0-11) [13](#0-12) 

### 运行模式检测

DataProvider 会根据当前运行模式（回测、模拟、实盘）自动路由到相应的数据源 [14](#0-13) 。

### 缓存机制

DataProvider 实现了多层缓存以优化性能：
- `__cached_pairs_backtesting` - 回测历史数据缓存
- `__cached_pairs` - 实时分析数据缓存  
- `__msg_cache` - 消息去重缓存 [15](#0-14) 

### 完整使用示例 [16](#0-15) 

## Notes

DataProvider 是 Freqtrade 数据管理系统的核心组件，它抽象了不同数据源的复杂性，为策略开发提供了统一的数据访问接口。在策略中通过 `self.dp` 访问，支持历史数据、实时数据、外部数据源等多种数据类型的获取和处理。
