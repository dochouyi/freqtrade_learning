`FreqaiDataDrawer` 是 FreqAI 机器学习框架中的核心组件之一，负责模型持久化、历史预测数据管理和元数据存储。 data_drawer.py:46-50

## FreqaiDataDrawer SDK 使用说明

### 概述

`FreqaiDataDrawer` 是一个持久化对象，在整个 FreqAI 生命周期中保持活跃，负责管理所有交易对的模型和信息。 data_drawer.py:47-50

### 初始化

```
from freqtrade.freqai.data_drawer import FreqaiDataDrawer  
from pathlib import Path  
  
# 初始化 FreqaiDataDrawer  
dd = FreqaiDataDrawer(full_path=Path("/path/to/models"), config=config)
```

data_drawer.py:70-107

### 核心数据结构

FreqaiDataDrawer 维护以下关键字典： data_drawer.py:74-82

- `pair_dict`: 存储所有交易对的元数据
- `model_dictionary`: 内存中的活跃推理模型
- `meta_data_dictionary`: 额外的元数据
- `historic_predictions`: 历史预测数据

### 主要功能

#### 1. 模型保存和加载

**保存模型数据：**

```
dd.save_data(model=trained_model, coin="BTC/USDT", dk=data_kitchen)
```

data_drawer.py:504-560

**加载模型数据：**

```
model = dd.load_data(coin="BTC/USDT", dk=data_kitchen)
```

data_drawer.py:572-630

#### 2. 历史预测管理

**保存历史预测：**

```
dd.save_historic_predictions_to_disk()
```

data_drawer.py:200-208

**加载历史预测：**

```
dd.load_historic_predictions_from_disk()
```

data_drawer.py:172-198

#### 3. 交易对信息管理

**获取交易对信息：**

```
model_filename, trained_timestamp = dd.get_pair_dict_info(pair="BTC/USDT")
```

data_drawer.py:247-268

#### 4. 预测数据追加

**追加模型预测：**

```
dd.append_model_predictions(  
    pair="BTC/USDT",  
    predictions=pred_df,  
    do_preds=do_predict_array,  
    dk=data_kitchen,  
    strat_df=strategy_dataframe  
)
```

data_drawer.py:333-398

#### 5. 指标跟踪

**更新指标：**

```
dd.update_metric_tracker(metric="accuracy", value=0.85, pair="BTC/USDT")
```

data_drawer.py:108-122

#### 6. 历史数据管理

**加载所有交易对历史：**

```
dd.load_all_pair_histories(timerange=time_range, dk=data_kitchen)
```

data_drawer.py:685-705

**更新历史数据：**

```
dd.update_historic_data(strategy=strategy, dk=data_kitchen)
```

data_drawer.py:632-683

### 文件结构管理

FreqaiDataDrawer 自动管理以下文件： data_drawer.py:83-89

- `historic_predictions.pkl`: 历史预测数据
- `pair_dictionary.json`: 交易对字典
- `global_metadata.json`: 全局元数据
- `metric_tracker.json`: 指标跟踪数据

### 支持的模型类型

FreqaiDataDrawer 支持多种模型保存格式： data_drawer.py:517-523

- `joblib`: 默认格式，适用于大多数机器学习库
- `keras`: Keras/TensorFlow 模型
- `stable_baselines3`: 强化学习模型
- `pytorch`: PyTorch 模型

### 线程安全

FreqaiDataDrawer 使用多个锁来确保线程安全： data_drawer.py:95-98

- `history_lock`: 历史数据锁
- `save_lock`: 保存操作锁
- `pair_dict_lock`: 交易对字典锁
- `metric_tracker_lock`: 指标跟踪锁

### 测试示例

在测试环境中的使用示例： conftest.py:111-114

```
def get_patched_data_drawer(mocker, freqaiconf):  
    dd = FreqaiDataDrawer(freqaiconf)  
    return dd
```

## Notes

FreqaiDataDrawer 是 FreqAI 架构中的三个核心组件之一，与 IFreqaiModel 和 FreqaiDataKitchen 协同工作。 freqai-developers.md:11-16 它专门负责数据持久化和模型管理，确保系统在崩溃后能够自动恢复，并维护完整的训练和预测历史记录。