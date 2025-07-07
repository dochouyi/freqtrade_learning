
https://deepwiki.com/search/pairlocks_4faa7dd7-5f9f-4bc8-b265-a819f93c7bcf

PairLocks的作用是防止交易对在特定时间段内被交易，这是Freqtrade中的一个核心风险管理机制。

## 主要功能

PairLocks系统提供以下核心功能：

**1. 交易对锁定机制**
PairLocks可以锁定特定的交易对，防止在锁定期间开启新的交易。 [1](#0-0) 

**2. 全局锁定支持**
系统支持全局锁定（使用"*"作为交易对名称），可以同时锁定所有交易对。 [2](#0-1) 

**3. 方向性锁定**
PairLocks支持按交易方向锁定，可以分别锁定多头（long）、空头（short）或双向（*）交易。 [3](#0-2) 

## 在交易流程中的应用

**交易创建时的检查**
在FreqtradeBot创建新交易时，会检查交易对是否被锁定： [4](#0-3) 

**全局锁定检查**
在进入交易位置前，系统会检查是否存在全局锁定： [5](#0-4) 

## 策略集成

策略可以通过以下方法与PairLocks交互：

**锁定交易对**： [6](#0-5) 

**解锁交易对**： [7](#0-6) 

**检查锁定状态**： [8](#0-7) 

## 用户界面支持

PairLocks通过多个用户界面提供管理功能：

**RPC接口**： [9](#0-8) 

**Telegram命令**： [10](#0-9) 

**REST API**： [11](#0-10) 

## Notes

PairLocks是Freqtrade风险管理系统的重要组成部分，与保护机制（Protections）紧密集成。它既支持数据库存储模式（用于实盘交易），也支持内存模式（用于回测）。 [12](#0-11) 锁定时间会自动向上舍入到下一个K线周期，确保时间边界的一致性。

Wiki pages you might want to explore:
- [Strategy System (freqtrade/freqtrade)](/wiki/freqtrade/freqtrade#2.2)
- [User Interfaces (freqtrade/freqtrade)](/wiki/freqtrade/freqtrade#4)













