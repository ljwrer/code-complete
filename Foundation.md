# Foundation
##  构建
### 构建活动的产物--源代码--往往是对软件的唯一精准描述
### 构建活动是唯一一项确保会完成的工作
## 隐喻
### 把软件开发和熟悉的活动联系在一起
* 智慧工具箱
* 房屋建设过程
## 前期准备
### 项目的成败很大程度在构建活动之前已经注定
* measure twice,cut once
### 开发中最常见的项目风险是糟糕的需求分析和糟糕的项目计划
### WISCA综合症
* 拒绝无效命令
* 假装在写代码
* 教育你的老板
* 换工作
### 论据
* 逻辑
    * 找出他真正想要的东西
* 类比
    * 食物链
        * 需求污染架构
        * 架构污染构建
* 数据
### 软件类型
* 商业系统
* 使命攸关的系统
* 性命攸关的嵌入式系统
### 开发方法
* 迭代式开发法
* 序列式开发法
### 问题定义
### 需求
* 开发过程能够帮助客户更好的理解自己的需求
    * 需求变更的主要来源
* 构建期间变更需求
    * 需求核对表评估需求质量
    * 确保每一个人都知道需求变更的代价
    * 建立一套变更控制程序
        * 需求变更委员会
    * 使用能适应变更的开发方法
        * 演进原型
        * 演进交付
    * 放弃这个项目
    * 注意项目的商业案例
        * 商业影响
* 需求核对表
    * 功能需求
        * 详细定义系统的全部输入/全部输出，输出格式
            * 来源、精准度、取值范围、出现频率、格式
        * 详细定义所有硬件及软件的外部接口
        * 定义全部外部通信接口
        * 列出用户想做的全部事情
        * 详细定义每个任务所用的数据以及每个任务得到的数据
    * 非功能需求(质量需求)
        * 为全部必要的操作,为用户的视角，详细描述了期望响应时间
        * 详细描述其他计时操作
            * 处理时间、数据传输率、系统吞吐量
        * 安全级别
        * 可靠性
            * 软件失灵的后果
            * 故障时重要信息的保护
            * 错误检测与恢复的策略
        * 硬件需求
            * 内存、磁盘
        * 系统的可维护性
            * 特定功能的变更
            * 操作环境的变更
            * 其他软件接口的变更
        * 对成功和失败的定义
    * 需求的质量
        * 需求是否用用户语言书写
        * 每条需求都不与其他需求冲突
        * 详细定义相互竞争的特性的权衡
            * 健壮性和正确性
        * 避免在需求中规定设计
        * 详细程度保持相当一致的水平
        * 足够清晰
            * 可转交给独立小组构建
        * 每个条款都与待解决的问题及其解决方案相关
            * 可上溯到问题的根源
        * 每条需求都是可测试的
            * 能进行独立的测试
        * 详细描述所有可能对需求的改动
            * 包括各项改动的可能性
### 架构
* 独立的文档描述架构
* 修复架构的时间成本和修复错误需求的时间成本处于同一数量级
* 组成部分
    * 程序组织
        * 构造块
            * 单个类
            * 多个类构成的子系统
            * 概要: 每条需求中的功能特性至少需要一个构造块覆盖
                * 明确各个构造块的责任
    * 主要的类
        * 类的责任
        * 与其他类交互
        * 继承体系、状态转换、对象持久化
        * 如何将类转化为子系统
    * 数据设计
        * 主要文件表和数据表的设计
            * 顺序访问列表、随机访问列表、堆栈、散列表
        * 数据库的高层组织结构和内容
    * 业务规则
    * 用户界面设计
        * 模块化
            * 需要做到砍掉交互界面的类、插入一组命令行的类
                * 单元测试
                * 子系统测试
    * 稀缺资源管理
        * 数据库连接
        * 线程
        * 句柄(handle)
        * 内存受限领域(驱动开发和嵌入式系统开发)
            * 内存管理
    * 安全性
        * 威胁模型
        * 缓冲区
        * 处理非受信数据
            * 用户输入
            * cookie
            * 配置数据(文件)
            * 外部接口输入
        * 保护内存中的秘密数据
    * 性能
        * 详细定义资源(速度、内存、成本)的优先顺序
        * 提供估计的数据及原因
        * 特定的算法和数据类型
    * 可伸缩性
        * 满足未来需求的能力
            * 用户数量增长
            * 服务器数量增长
            * 网络节点数量增长
            * 数据库记录数
            * 数据库记录长度
    * 国际化/本地化
        * i18n/l10n
        * 字符串问题和字符集问题
        * 字符串类型
        * 方案
            * 直接嵌入
            * 封装入类
            * 存入资源文件
    * 输入输出
        * 读取策略
            * look-ahead
            * look-behind
            * just in time
        * 监测I/O错误
            * 字段、记录、流、文件
    * 错误处理
        * 90%的代码是用来处理异常情况、错误处理及簿记(housekeeping)工作
        * 一致性处理错误策略
            * 在架构层面处理错误而不是代码约定层次
            * 策略
                * 纠正还是检测
                * 主动还是被动
                    * 主动
                        * 如检查用户输入
                    * 被动
                        * 如数值溢出
                * 错误传播
                    * 立即丢弃引发错误的数据
                    * 进入错误处理状态
                    * 延迟错误报告
                * 错误消息
                    * 建立一套有关错误消息的约定
                * 处理异常
                    * 何时抛出
                    * 何时捕获
                    * 如何log
                    * 如何在文档中描述
                    * 处理层次
                        * 发现时处理
                        * 传递到专门处理错误的类处理
                        * 沿着函数调用链传递
                * 输入数据验证
                    * 每个类单独验证
                    * 一组类负责验证整个系统的数据有效性
                    * 某个层次上的类是否假设接受的数据是clean的
                * 错误机制
                    * 使用运行环境内建
                    * 建立自己的机制
    * 容错性(增强系统可靠性)
        * 检测错误
        * 从错误中恢复
        * 部分运转
        * 功能退化
    * 可行性
        * 验证概念原型
    * 过度工程
        * 在软件中，链条的强度不是取决于最薄弱的一环，而是等于所有薄弱环节的乘积
    * 造还是买
        * 应该说明自己定制的组件在哪些方面胜过现成的程序库和组件
    * 复用
        * 说明如何对需要复用的软件加工，使之符合其他架构目标
    * 变更策略
        * 清楚的描述处理变更的策略
            * 考虑可能会有所增强的功能
            * 单一的变更只会影响少数几个类
            * 输入输出格式、用户交互的风格、需求的处理
                * 文件加入版本号
                * 保留字段
                * delay commitment
* 总体质量
    * 每一项变更干净的融入整体概念
    * 描述所有主要决策的冬季,谨防“我们向来这么做”
    * 避免提前做构建设计期间的工作
    * 处于欠描述和过度描述之间
    * 指出风险区域
    * 包含多个视角
    * 不包含任何难以理解的部分
    * 独立于用作实现架构的机器和语言
### 时间长度
* 前期准备投入10%-20%的工作量和20%-30%的时间
* 如有必要，将分析工作和架构工作作为独立的项目来做
## 构建决策
### 编程语言
* Sapir-Whorf假说
* > 你思考的能力取决于你是否知道能够表达该思想的词汇

### 编程约定
* 变量名、类名、子程序名、格式约定、注释约定
* 各个具体部件都能反映整体架构的内涵
### 技术浪潮中的位置
* 深入一种语言去编程
    * 大多数重要的编程原则并不依赖特定的语言
    * 发明自己的编程约定、标准和类库
### 团队工作
* 集成工序
* 结对编程、独自编程
### 质量保证
* 单元测试
* check in流程
    * 调试器单步跟踪
    * 集成测试
* review
### 工具
* vcs
* 语言版本
* 编程框架
* 非标准语言特性
* 编辑器、重构工具、调试器、测试框架、语法检查器

*XMind: ZEN - Trial Version*