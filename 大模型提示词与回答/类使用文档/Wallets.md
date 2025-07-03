这里的 `Wallets` 类是 Freqtrade 交易机器人中用于管理钱包余额和持仓的核心组件。 wallets.py:36-37

## Wallets 类 SDK 使用说明

### 概述

`Wallets` 类是 Freqtrade 中负责管理交易账户余额、持仓信息和资金状态的核心组件 wallets.py:36-54 。它支持现货和期货交易模式，并能在实盘、模拟盘和回测模式下正常工作。

### 初始化

```
from freqtrade.wallets import Wallets  
from freqtrade.exchange import Exchange  
  
# 初始化钱包管理器  
wallets = Wallets(config, exchange, is_backtest=False)
```

wallets.py:37-53

### 核心数据结构

#### Wallet 钱包对象 wallets.py:21-26

#### PositionWallet 持仓对象 wallets.py:28-34

### 主要方法

#### 1. 获取余额信息

```
# 获取可用余额  
free_balance = wallets.get_free('USDT')  
  
# 获取已使用余额（挂单占用）  
used_balance = wallets.get_used('USDT')   
  
# 获取总余额  
total_balance = wallets.get_total('USDT')
```

wallets.py:55-74

#### 2. 获取所有余额和持仓

```
# 获取所有币种余额  
all_balances = wallets.get_all_balances()  
  
# 获取所有持仓（期货模式）  
all_positions = wallets.get_all_positions()
```

wallets.py:233-237

#### 3. 更新钱包数据

```
# 强制更新钱包数据  
wallets.update(require_update=True)  
  
# 允许跳过更新（如果最近已更新）  
wallets.update(require_update=False)
```

wallets.py:212-231

#### 4. 获取抵押品信息（期货交易）

```
# 获取总抵押品金额  
collateral = wallets.get_collateral()
```

wallets.py:76-86

#### 5. 获取持有资产

```
# 获取特定交易对的持有数量  
owned_amount = wallets.get_owned('BTC/USDT', 'BTC')
```

wallets.py:88-97

### 在策略中使用

在 Freqtrade 策略中，`wallets` 对象会自动注入到策略实例中 freqtradebot.py:130-131 ：

```
class MyStrategy(IStrategy):  
    def custom_stake_amount(self, pair, current_time, current_rate,   
                          proposed_stake, min_stake, max_stake,   
                          leverage, entry_tag, side, **kwargs):  
        # 检查钱包是否可用  
        if self.wallets:  
            free_usdt = self.wallets.get_free('USDT')  
            total_usdt = self.wallets.get_total('USDT')  
              
            # 基于可用余额调整仓位大小  
            if free_usdt > 1000:  
                return proposed_stake * 1.5  
                  
        return proposed_stake
```

strategy-customization.md:999-1004

### 不同运行模式的行为差异

#### 实盘/模拟盘模式

- 直接从交易所获取实时余额数据 wallets.py:179-210
- 支持实时持仓信息更新

#### 回测模式

- 基于配置的初始资金和交易历史计算余额 wallets.py:99-177
- 模拟真实的资金变化过程

### 注意事项

1. **安全检查**: 在策略中使用前务必检查 `wallets` 对象是否存在 strategy-customization.md:997
2. **更新频率**: 钱包数据会定期自动更新，但在关键操作前可手动触发更新 freqtradebot.py:2012-2013
3. **模式差异**: 在不同的运行模式下，钱包行为会有所不同，特别是在回测和实盘之间 strategy-customization.md:992-995

## Notes

`Wallets` 类是 Freqtrade 架构中的核心组件，与 `FreqtradeBot` 主类紧密集成。它不仅管理资金状态，还参与风险控制和仓位管理。在期货交易中，它还负责处理保证金和抵押品计算。该类的设计考虑了多种交易模式和运行环境的兼容性。