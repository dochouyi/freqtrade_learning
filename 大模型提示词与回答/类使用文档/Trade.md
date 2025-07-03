## Trade 类 SDK 使用说明文档

### 概述

`Trade` 类是 Freqtrade 的核心数据模型，用于持久化存储交易信息到数据库中 trade_model.py:1-3 。它继承自 `LocalTrade` 类，提供了数据库特定的功能 trade_model.py:1642-1648 。

### 基本属性

Trade 对象包含以下核心属性 trade-object.md:14-40 ：

- `pair`: 交易对名称
- `is_open`: 交易是否仍在进行中
- `open_rate`: 入场价格（平均入场价格）
- `close_rate`: 出场价格
- `stake_amount`: 投入金额（以报价货币计算）
- `amount`: 持有的基础货币数量
- `leverage`: 杠杆倍数
- `is_short`: 是否为空头交易
- `orders`: 关联的订单列表

### 创建 Trade 实例

#### 在回测中创建 backtesting.py:1143-1170

#### 从 JSON 创建

您可以使用 `from_json()` 方法从 JSON 字符串创建 Trade 实例： trade_model.py:1541-1549

### 核心方法

#### 查询方法

**获取交易代理** trade_model.py:1771-1804

使用示例：

```python
from freqtrade.persistence import Trade  
from datetime import timedelta  
  
# 获取特定交易对的历史交易  
trade_hist = Trade.get_trades_proxy(pair='ETH/USDT', is_open=False, open_date=current_date - timedelta(days=2))
```

**获取开放交易数量** trade-object.md:72-80

**获取总利润** trade-object.md:82-90

#### 数据序列化

**转换为 JSON** trade_model.py:665-672

**转换为字典**
Trade 对象的 `to_json()` 方法返回包含所有交易信息的字典 trade_model.py:674-763 。

### 自定义数据存储

Trade 类支持存储用户自定义数据，这些数据会持久化到数据库中： strategy-advanced.md:16-21

#### 存储自定义数据

```python
# 存储数据  
trade.set_custom_data(key='entry_type', value='breakout')  
  
# 获取数据  
entry_type = trade.get_custom_data(key='entry_type')  
  
# 获取数据条目（包含元数据）  
entry = trade.get_custom_data_entry(key='entry_type')
```

strategy-advanced.md:94-101

### 订单管理

Trade 对象包含订单列表，提供多种订单相关属性： trade_model.py:613-642

### 数据库操作

#### 提交更改 trade_model.py:1762-1764

#### 删除交易 trade_model.py:1753-1760

### REST API 集成

Trade 数据可以通过 REST API 访问： ft_rest_client.py:298-304

### 使用示例

#### 在策略中访问交易信息 strategy-advanced.md:29-39

#### 测试中的使用 test_trade_fromjson.py:10-25

### Notes

Trade 类是 Freqtrade 交易系统的核心，提供了完整的交易生命周期管理。在回测模式下使用 `LocalTrade`，在实盘交易中使用 `Trade` 类进行数据库持久化。所有的交易操作都应该通过这个类的方法进行，以确保数据一致性和完整性。