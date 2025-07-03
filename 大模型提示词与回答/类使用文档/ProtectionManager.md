基于代码分析，`ProtectionManager` 是 Freqtrade 交易机器人中负责风险保护管理的核心组件，位于 `freqtrade/plugins/protectionmanager.py` 中。 protectionmanager.py:20-36

## ProtectionManager SDK 使用说明

### 概述

`ProtectionManager` 是 Freqtrade 中的保护机制管理器，用于防止策略在不利市场条件下继续交易，通过临时锁定交易对或全局停止交易来保护资金。 protections.md:1-4

### 初始化

```
from freqtrade.plugins.protectionmanager import ProtectionManager  
  
# 初始化保护管理器  
protection_manager = ProtectionManager(config, protections_list)
```

protectionmanager.py:21-35

### 核心方法

#### 1. 全局停止检查

```
# 检查是否需要全局停止交易  
result = protection_manager.global_stop(now=datetime.now(timezone.utc), side="long")
```

protectionmanager.py:50-62

#### 2. 单对停止检查

```
# 检查特定交易对是否需要停止交易  
result = protection_manager.stop_per_pair("BTC/USDT", now=datetime.now(timezone.utc), side="long")
```

protectionmanager.py:64-78

#### 3. 获取保护处理器信息

```
# 获取已加载的保护处理器名称列表  
names = protection_manager.name_list  
  
# 获取保护处理器的简短描述  
descriptions = protection_manager.short_desc()
```

protectionmanager.py:37-48

### 可用保护类型

系统支持以下保护机制： protections.md:14-19

1. **StoplossGuard** - 止损保护
2. **MaxDrawdown** - 最大回撤保护
3. **LowProfitPairs** - 低盈利交易对保护
4. **CooldownPeriod** - 冷却期保护

### 配置验证

`ProtectionManager` 提供静态方法验证保护配置的有效性： protectionmanager.py:80-115

```
# 验证保护配置  
ProtectionManager.validate_protections(protections_config)
```

### 在 FreqtradeBot 中的集成

`ProtectionManager` 在 `FreqtradeBot` 中被初始化并用于处理保护逻辑： freqtradebot.py:177

交易完成后会触发保护检查： freqtradebot.py:2399-2418

### 配置示例

```
protections = [  
    {  
        "method": "StoplossGuard",  
        "lookback_period_candles": 24,  
        "trade_limit": 4,  
        "stop_duration_candles": 4,  
        "only_per_pair": False  
    },  
    {  
        "method": "CooldownPeriod",   
        "stop_duration_candles": 2  
    }  
]
```

protections.md:50-60

## Notes

`ProtectionManager` 通过 `ProtectionResolver` 动态加载保护处理器 protection_resolver.py:27-44 ，每个保护处理器都继承自 `IProtection` 接口 iprotection.py:25-29 。系统支持基于时间和蜡烛数量的配置方式，并提供完整的测试覆盖 test_protections.py:93-105 。