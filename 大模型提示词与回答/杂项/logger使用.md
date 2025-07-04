https://deepwiki.com/search/freqtradelogger-logginggetlogg_b18f25d1-33bc-45c8-8872-272cd3dbcc6e

# freqtrade中logger = logging.getLogger(__name__)是什么原理，在哪里调用到logging的

## Answer

在freqtrade中，`logger = logging.getLogger(__name__)` 是Python标准日志系统的使用模式，用于为每个模块创建独立的日志记录器。

### 原理说明

`logging.getLogger(__name__)` 的工作原理是：
- `__name__` 是Python内置变量，包含当前模块的完整路径名（如 `freqtrade.configuration.configuration`）
- `logging.getLogger()` 根据这个名称创建或获取一个日志记录器实例
- 这样每个模块都有自己的日志记录器，可以独立控制日志级别和格式

### 在freqtrade中的使用

这个模式在freqtrade代码库中广泛使用，几乎每个模块都有这样的声明： [1](#0-0) [2](#0-1) [3](#0-2) 

### 日志系统的初始化和配置

日志系统在freqtrade启动时通过以下流程初始化：

1. **预初始化阶段**：在 `main.py` 中调用 `setup_logging_pre()` [4](#0-3) 

2. **完整初始化**：通过 `setup_logging()` 函数配置完整的日志系统 [5](#0-4) 

3. **配置加载**：日志配置通过 `Configuration` 类处理，支持从配置文件、环境变量等多种来源加载日志设置

### 实际调用链路

当你在代码中使用 `logger.info()` 等方法时，调用链路如下：

1. 模块中的 `logger` 实例（通过 `logging.getLogger(__name__)` 创建）
2. Python标准库的 `logging` 模块处理日志消息
3. 根据配置的处理器（handlers）输出到控制台、文件或其他目标

例如在 `worker.py` 中的使用： [6](#0-5) 

### 日志配置示例

freqtrade支持通过配置文件自定义日志格式和输出目标，默认配置包括控制台输出和可选的文件输出： [7](#0-6) 

## Notes

freqtrade的日志系统还支持高级功能如系统日志（syslog）输出、Rich格式化输出、以及通过缓冲处理器支持API端点访问日志等功能。日志级别可以通过命令行参数 `-v` 或配置文件中的 `verbosity` 设置来控制。

Wiki pages you might want to explore:
- [Configuration System (freqtrade/freqtrade)](/wiki/freqtrade/freqtrade#1.2)
- [User Interfaces (freqtrade/freqtrade)](/wiki/freqtrade/freqtrade#4)
- [Testing Framework (freqtrade/freqtrade)](/wiki/freqtrade/freqtrade#6.2)