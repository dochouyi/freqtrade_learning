## FreqAI配置参数总结

### 通用配置参数 (freqai) [1](#0-0) 

- `freqai` - **必需**，包含所有FreqAI控制参数的父字典
- `train_period_days` - **必需**，训练数据使用的天数（滑动窗口宽度）
- `backtest_period_days` - **必需**，从训练模型推理的天数，然后滑动训练窗口并重新训练
- `identifier` - **必需**，当前模型的唯一ID，用于模型保存和重载
- `live_retrain_hours` - 干运行/实盘运行期间的重训练频率，默认0（尽可能频繁重训练）
- `expiration_hours` - 避免使用超过指定小时数的旧模型进行预测，默认0（模型永不过期）
- `purge_old_models` - 磁盘上保留的模型数量，默认2
- `save_backtest_models` - 回测时是否保存模型到磁盘，默认False
- `fit_live_predictions_candles` - 用于计算目标统计的历史蜡烛数量
- `continual_learning` - 使用最近训练模型的最终状态作为新模型起点，默认False
- `write_metrics_to_disk` - 收集训练时间、推理时间和CPU使用情况到json文件，默认False
- `data_kitchen_thread_count` - 数据处理专用线程数
- `activate_tensorboard` - 是否激活tensorboard，默认True
- `wait_for_training_iteration_on_reload` - 重载时是否等待当前训练迭代完成，默认True

### 特征参数 (feature_parameters) [2](#0-1) 

- `feature_parameters` - 包含特征工程参数的字典
- `include_timeframes` - 所有指标将创建的时间框架列表
- `include_corr_pairlist` - 作为附加特征添加的相关币种列表
- `label_period_candles` - 创建标签的未来蜡烛数量
- `include_shifted_candles` - 添加历史蜡烛特征的数量
- `weight_factor` - 根据时间近期性对训练数据点加权
- `indicator_periods_candles` - 计算指标的时间周期
- `principal_component_analysis` - 使用PCA自动降维，默认False
- `plot_feature_importances` - 为每个模型创建特征重要性图，默认0
- `DI_threshold` - 激活异常值检测的相异性指数阈值
- `use_SVM_to_remove_outliers` - 使用SVM检测和移除异常值
- `svm_params` - SVM参数字典
- `use_DBSCAN_to_remove_outliers` - 使用DBSCAN聚类移除异常值
- `noise_standard_deviation` - 添加噪声防止过拟合，默认0
- `outlier_protection_percentage` - 异常值保护百分比，默认30
- `reverse_train_test_order` - 反转训练测试顺序，默认False
- `shuffle_after_split` - 分割后打乱数据，默认False
- `buffer_train_data_candles` - 缓冲训练数据蜡烛数，默认0

### 数据分割参数 (data_split_parameters) [3](#0-2) 

- `data_split_parameters` - 包含scikit-learn test_train_split()的参数
- `test_size` - 用于测试而非训练的数据比例
- `shuffle` - 训练时是否打乱数据点，默认False

### 模型训练参数 (model_training_parameters) [4](#0-3) 

- `model_training_parameters` - 包含所选模型库可用参数的灵活字典
- `n_estimators` - 模型训练中拟合的提升树数量
- `learning_rate` - 模型训练期间的提升学习率
- `n_jobs`, `thread_count`, `task_type` - 并行处理线程数和任务类型设置

### 强化学习参数 (rl_config) [5](#0-4) 

- `rl_config` - 强化学习模型控制参数字典
- `train_cycles` - 训练时间步数设置
- `max_trade_duration_candles` - 指导代理训练保持交易在期望长度以下
- `model_type` - stable_baselines3或SBcontrib的模型字符串
- `policy_type` - stable_baselines3可用策略类型之一
- `max_training_drawdown_pct` - 代理训练期间允许的最大回撤，默认0.8
- `cpu_count` - 强化学习训练进程专用线程/CPU数量
- `model_reward_parameters` - 自定义calculate_reward()函数中使用的参数
- `add_state_info` - 是否在特征集中包含状态信息，默认False
- `net_arch` - 网络架构，默认[128, 128]
- `randomize_starting_position` - 随机化每个episode起始点，默认False
- `drop_ohlc_from_features` - 不在特征集中包含标准化OHLC数据，默认False
- `progress_bar` - 显示进度条，默认False

### PyTorch参数 [6](#0-5) 

- `learning_rate` - 传递给优化器的学习率，默认3e-4
- `model_kwargs` - 传递给模型类的参数，默认{}
- `trainer_kwargs` - 传递给训练器类的参数，默认{}
- `n_epochs` - 训练循环中的epoch数量，默认10
- `n_steps` - 训练迭代次数的替代设置方式
- `batch_size` - 训练期间使用的批次大小，默认64

### 附加参数 [7](#0-6) 

- `keras` - 如果模型使用Keras需要激活此标志，默认False
- `conv_width` - 神经网络输入张量宽度，默认2
- `reduce_df_footprint` - 重新转换数值列以减少内存使用，默认False

## Notes

这些配置参数定义在FreqAI的配置架构中 [8](#0-7) ，并在文档中详细说明了每个参数的用途和默认值。完整的配置示例可以在`config_examples/config_freqai.example.json`中找到。
