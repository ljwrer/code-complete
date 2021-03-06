# Variables

## 一般事项

### 变量定义

- 隐式声明

	- 危险
	- 关闭隐式声明
	- 声明全部的变量
	- 遵循某种命名规则
	- 检查变量名

		- 生成交叉引用列表

### 变量初始化

- 问题

	- 未对变量赋值
	- 变量值已过期
	- 变量一部分被赋值

		- 指针

- 建议

	- 声明变量的时候初始化
	- 若不支持，则在靠近变量第一次使用的位置初始化它

		- 就近原则

	- 在靠近第一次使用变量的位置声明和定义该变量
	- 尽量使用final或者const
	- 注意计数器和累加器
	- 在类的构造函数里初始化该类的数据成员
	- 检查是否需要重新初始化
	- 一次性初始化具名常量

		- 用可执行代码来初始化变量

			- startUp()

	- 使用编译器设置来自动初始化所有变量

		- 编译器依赖

	- 利用编译器的警告信息
	- 检查输入参数的合法性
	- 使用内存访问工具检查错误的指针
	- 程序开始时初始化工作内存

		- 预填充工具

			- 如填0，0xCC

		- 填充工具晃动
		- 启动时初始化工作内存

			- 隐藏缺陷

### 作用域

- 变量引用局部化

	- 攻击窗口
	- 跨度

- 缩短存活时间

	- 对代码更准确的认识
	- 减少初始化错误的可能
	- 可读性
	- 便于重构

- 全局变量跨度和生存时间都很长
- 减小作用域

	- 循环开始之前再初始化循环里使用的变量
	- 直到变量即将被使用时再为其赋值
	- 相关语句放在一起
	- 相关语句提取成单独的子程序
	- 开始时采用最严格的可见性
	- 平衡方便性和智力可管理性

### 持续性

- 形态

	- 特定代码段或子程序的生命期

		- for循环

	- 只要允许就会持续下去

		- c++ delete之前的对象

	- 程序生命期

		- static

	- 永远持续

		- 数据库

- 变量实际生命期比你想象的短

	- 调试代码或断言
	- 抛弃变量时置空

		- null

	- 编写代码时假设数据没有持续性

		- 支持static的语言例外

	- 养成声明和初始化的习惯

### 绑定时间

- 绑定越晚越灵活但程序复杂度增加
- 时间

	- 编码时

		- magic number

	- 编译时

		- 具名常量

	- 加载时

		- 从注册表，外部文件读取

	- 对象实例化时

		- 创建弹窗时读取

	- 即使

		- 弹窗重绘时读取

- 平衡灵活性和复杂度

### 数据类型和控制结构

- 序列型数据

	- 顺序语句

- 选择型数据

	- if,case

- 迭代行数据

	- 循环

		- 容器，记录，数组

- 组合型数据

### 单一用途

- 不要为了节省空间破坏程序可读性和可维护性
- 避免代码具有隐式含义

	- 双重用途

		- 如-1表示出错

- 使用所有已声明的变量

## 变量名的力量

### 可读、易记、恰如其分

### 注意事项

- 对变量的描述就是最佳的变量名
- 以问题为导向

	- 反映问题本身，而不是解决方案
	- 直指问题领域，与计算的世界无关

- 适当的名字长度

	- 8-20
	- 10-16最佳

- 作用域的影响

	- 较长的名字

		- 全局变量
		- 使用少的变量

	- 较短的名字

		- 局部变量
		- 循环变量

	- 全局命名空间

		- 限定词
		- namespace
		- package
		- 子系统特征前缀

- 计算值限定词

	- 限定词加到名字最后

		- total
		- sum
		- average
		- max
		- min
		- string

	- 主要含义的部分位于最前面

		- costTotal
		- costAverage
		- 例外

			- num放在变量名开始位置代表总数

				- 使用count或total代表总数
				- 使用index特指

- 对仗词

	- begin/end
	- first/last
	- locked/unlocked

### 特定类型的数据命名

- 循环下标

	- i,j,k
	- 循环之外使用

		- 使用有意义的名字

	- 循环嵌套容易下标串话

		- 使用有意义的名字

- 状态变量

	- 使用比flag更好的名字

		- 枚举类型或具名常量
		- 值比较

- 临时变量

	- 谨慎使用temp

- 布尔变量

	- 典型变量名

		- done
		- error
		- found
		- success/ok

	- 隐含“真/假”含义

		- status -> statusOK
		- sourceFile -> sourceFileFound
		- is

			- 避免使用了模糊的名字
			- 降低了简单逻辑表达式的可读性

	- 使用肯定的布尔变量名

		- 避免双重否定

- 枚举类型

	- 组前缀

		- Color_
		- Plant_

	- 类

		- Color.Red

- 常量

	- 使用常量含义而不是值的含义

### 命名规则的力量

- 好处

	- 全局决策
	- 项目之间传递
	- 新项目中快速学习
	- 减少名字增生

		- 避免给一个变量取两个名字

	- 弥补编程语言的不足

		- 如作用域机制有缺陷的语言

	- 强调相关变量之间的关系

- 规则的存在为代码增加了结构，减少需要考虑的事情
- 时机

	- 多人合作开发
	- 项目交接
	- 程序评估
	- 程序生命期足够长
	- 项目存在不常见的术语

- 正式程度取决于项目实际情况

### 非正式命名规则

- 语言无关的指导原则

	- 区分变量名和子程序名字

		- 变量名，对象名小写字母开头
		- 子程序以大写字母开头

	- 区分类和对象

		- 通过变量采用更明确的名字区分类型和变量

	- 标识全局变量

		- g_前缀

	- 标识成员变量

		- m_前缀

	- 标识类型声明

		- t_
		- C++ 使用大写

			- typedef
			- struct

	- 标识具名常量

		- c_
		- C++/Java

			- 全部大写，下划线分隔

	- 标识枚举类型

		- 全部大写
		- 或者e_,E_
		- 类型前缀

			- Color_

	- 再不能保证输入参数只读的语言里标识只读参数

		- const前缀

	- 格式化命名提高可读性

		- 大小写和分隔符

			- 优先采用大小写

- 语言相关的指导原则

	- C（略）
	- C++（略）
	- VB(略)
	- Java

		- i,j是整数下标
		- 常量全部大写并用下划线分隔
		- 类和接口每个单词首字母大写
		- 变量名和方法名第一个首字母小写
		- 除了全部大写的名字外不使用分隔符
		- 访问器子程序使用get和set前缀

	- 混编语言

		- 优化以保持整体一致性和可读性

	- 建立命名规则示例

		- 实体+描述
		- 变量名内容

			- 变量的内容
			- 数据的种类
			- 变量的作用域

### 标准前缀

- 匈牙利命名法
- 用户自定义类型（UDT）

	- 标识命名对象或变量

		- 窗体
		- 屏幕区域
		- 字体

	- 不表示编程语言预置数据类型
	- 示例

		- ch

			- 字符

				- chCursorPosition

		- doc

			- 文档

				- docActive

		- pa

			- 段落

				- firstPaActiveDocument

		- scr

			- 屏幕区域

				- scrUserWorkspace

		- wn

			- 窗体

				- wnMain

- 语义前缀

	- 标准语义前缀

		- c

			- 数量count

		- first

			- 数组第一个元素

		- g

			- 全局变量global

		- i

			- 数组下标i

		- m

			- 成员变量member

		- max

			- 数据绝对的最后一个元素

		- p

			- 指针

	- 根据需要和UDT结合使用
	- 优点

		- 精确的描述模糊的名字
		- 名字更紧凑
		- 对类型作出判断

	- 缺陷

		- 容易在使用前缀的同时忽略给变量起有意义的名字

### 具有可读性的短名字

- 没有任何理由去缩短具有丰富含义的名字
- 现代编程语言很少需要用到缩写
- 指导原则

	- 标准缩写
	- 去掉前置元音

		- computer->cmptr
		- screen->scrn

	- 去掉虚词

		- and
		- or
		- the

	- 使用每个单词的第一个或前几个字母
	- 统一地在每个单词的第一、第二或第三个字母后截断
	- 保留每个单词的第一个和最后一个字母
	- 使用名字中的每一个重要单词，最多不超过三个
	- 去除无用的后缀

		- ing,ed

	- 保留每个音节中最引人注意的发音
	- 确保不要改变变量的含义
	- 反复使用以上技术，直到每个变量名长度缩减到8-20个字符

- 语音缩写

	- 不推荐

- 注意事项

	- 不要用从每个单词中删除一个字符的方式来缩写
	- 保持缩写一致
	- 创建可读的名字

		- xPstn -> xPos

			- 电话测试

	- 避免使用容易看错或读错的字符组合

		- 可用分隔符

	- 使用辞典来解决命名冲突

		- 使用含义相同的不同单词避免命名冲突

	- 在代码里添加缩写对照表解释极短的名字的含义
	- 在一份项目级的标准缩写文档中说明所有的缩写

		- 缩写风险

			- 读者不理解
			- 程序员用多个缩写来代表相同的词

	- 名字对于代码读者的意义要比对作者更重要

### 应该避免的名字

- 指导原则

	- 避免使用令人误解的名字或缩写
	- 避免使用具有相似含义的名字
	- 避免使用不同含义却有相似名字的变量

		- 采用至少有两个字母不同的名字
		- 把不用之处放在名字的开始或者结尾

	- 避免使用发音相近的名字

		- 电话测试

	- 避免在名字中使用数字

		- 如果数字是有意义的，则使用数组
		- 如果现实名字中有数字，则使用数字

			- 319国道 -> road319

	- 避免在单词中拼错单词
	- 避免使用英语中常常拼错的单词

		- absense,acsend

	- 不要仅靠大小写来区分变量名

		- 保持名字唯一

	- 避免使用多种自然语言

		- colour -> color

	- 避免使用标准类型、变量和子程序的名字
	- 不要使用与变量含义完全无关的名字
	- 避免在名字中包含易混淆的字符

		- 含易混淆的字符

			- l,1,I
			- .,
			- 0O
			- 2Z
			- :;
			- S5
			- G6

		- Fortran Format句号事件

## 基本数据类型

### 数值

- 避免magic number
- 可以使用硬编码的0或1
- 预防除零错误
- 显示类型转换
- 避免混合类型比较
- 注意编译器警告

### 整数

- 检查整数除法
- 检查整数溢出
- 检查中间结果溢出

### 浮点数

- 避免数量级相差巨大的数之间的加减运算

	- 先排升序再相加

		- 逆向求和运算

- 避免等值判断

	- 确定可接受的精度，设计equals函数

		- 动态决定精度

- 处理舍入问题

	- 换用高精度变量类型
	- 换用二进制编码的十进制

		- BCD编码

	- 把浮点变量变成整数变量

		- 创建隐藏整数表示并且支持必要数字运算的类

	- 检查语言和函数库对特定数据类型的支持

		- Currency

### 字符和字符串

- 避免magic character

	- 便于修改
	- i18n
	- 节省存储空间

		- 独立于源码

	- 字面量含义模糊

- 避免off-by-one
- 了解语言对unicode支持
- 尽早决定国际化/本地化策略
- 根据字符集决定unicode或者ios8859
- 采用某种一致的字符串类型转换策略
- c语言字符串

	- 注意字符串指针和字符数组之间的差异

		- 警惕任何包含字符串和等号的表达式
		- 通过命名规则区分变量是字符串还是字符串指针

	- 把C-style字符串的长度声明为CONSTANT+1

		- 空结尾符

			- 具名常量所有字符串

	- 用null初始化字符串以避免无结束符的字符串

		- 或者初始化为0，用calloc动态分配内存

	- 用字符数组取代C中的指针

		- 避免指针错误

	- 用strlcpy取代strcpy以避免无结束符的字符串

### 布尔变量

- 用布尔变量对程序加以文档说明

	- 表达式结果付给变量

### 枚举类型

- 提高可读性

	- 数字字面量 -> 枚举
	- 定义子程序参数

- 提高可靠性

	- 编译器类型检查

- 简化修改
- 作为布尔变量的替换方案
- 检查非法值

	- switch default

- 定义除枚举的第一项和最后一项，以便于循环边界
- 把枚举类型的第一个元素留做非法值
- 明确定义项目代码编写标准中第一个和最后一个元素的使用规则，并在使用时保持一致
- 警惕给枚举元素明确赋值带来的失误
- 使用全局变量或类模拟枚举

	- static final

### 具名常量

- 程序参数化

	- 单点控制

- 数据声明中使用具名常量

	- 集中控制

- 避免使用文字量，即使是安全的
- 用具有适当作用域的变量或类来模拟具名常量

	- 局部->类->全局

- 统一地使用具名常量

### 数组

- 下标越界
- 考虑用容器取代数组，将数组作为顺序化结构来处理

	- 集合
	- 栈
	- 队列

- 检查数组的边界点
- 多维数组下标使用有意义的名字
- 提防下标串话
- 在C中结合ARRAY_LENGTH()宏来使用数组

	- sizeof

### 创建自己的类型

- 信息隐藏
- 避免过多的信息分发
- 增加可靠性
- 弥补语言的不足

	- typedef int Boolean

- 指导原则

	- 给所创建的类型取功能导向的名字

		- 避免计算机底层
		- 反映现实世界问题

			- 提供程序与实现语言的绝缘层
			- 容易修改

	- 避免使用预定义类型
	- 不要重定义一个预定义类型
	- 定义替代类型以便于移植

		- INT32->LONG64

	- 考虑创建一个类而不是使用typedef

## 不常见的数据类型

### 非现代面向对象编程语言

### 结构体

- 明确数据关系
- 简化数据块操作
- 简化参数列表（如有必要）
- 减少维护

### 指针

- 理解编译器内存管理机制
- 理解指针

	- 指针内容

		- 内存中的某处位置
		- 如何解释该位置的内容

			- 基类型决定内容将解释
			- 内存并不包含任何与之相关联的内在的解释

- 一般技巧

	- 错误定位

		- 指针指向不该指向的位置
		- 指针错误的症状常常与引起指针错误的原因无关

	- 双向策略

		- 避免造成指针错误
		- 尽快检测出指针错误

	- 把指针操作限制在子程序或者类里面
	- 同时声明和定义指针
	- 在与指针分配相同的作用域中删除指针
	- 在使用指针之前检查指针

		- 访问器子程序

	- 先检查指针所引用的变量再使用
	- 用狗牌字段来检测损毁的内存

		- 开始位置检测是否多执行了释放该内存的操作
		- 放在后面检测超出该内存块末尾的覆盖数据操作

	- 增加明显冗余

		- 特定字段重复两次

	- 用额外的指针变量提高代码清晰度

		- 不要节约使用指针变量

			- 尤其是链表操作

	- 简化复杂的指针表达式
	- 画图
	- 按照正确的顺序删除链表中的指针
	- 分配一片保留的内存后备区域

		- 用户和用户数据

	- 粉碎垃圾数据

		- c

			- 释放前用垃圾数据覆盖

	- 删除或释放指针之后把它们设为空值
	- 删除变量之前检查非法指针

		- 避免删除空指针

	- 跟踪指针分配情况

		- 维护指针分配列表

	- 编写覆盖子程序，集中实现避免指针问题的策略

		- SAFE_NEW
		- SAFE_DELETE

	- 采用非指针技术

- C++指针

	- 理解指针与引用的区别

		- 指针*

			- obj->filed

		- 引用&

			- obj.field

		- 引用总是必须引用对象，指针可以为空
		- 引用所指向的对象在该引用初始化后不能改变

	- 指针用于引用传递参数，const引用用于值传递参数

		- const引用难以传播
		- 传值

			- 不能修改传入的对象

	- 使用auto_ptr
	- 灵活运用智能指针

- C指针

	- 使用显示指针类型而不是默认类型
	- 避免强制类型转换
	- 遵循参数传递的星号规则
	- 在内存分配中使用sizeof()确定变量的大小

### 全局变量

- 常见问题

	- 无意间修改
	- 别名问题
	- 代码重入问题

		- 多线程环境

	- 阻碍代码重用
	- 初始化顺序不确定引发问题
	- 破坏了模块化和智力上对的可管理性

- 使用理由

	- 保存全局数据
	- 模拟具名常量
	- 模拟枚举类型
	- 简化对极其常用的数据的使用
	- 消除流浪数据

		- 传递而不使用的参数

- 替换方案

	- 现设为局部，需要时再设为全局
	- 区分全局变量和类变量

		- 不要直接访问类变量

	- 使用访问器子程序

- 访问器子程序

	- 优势

		- 数据集中控制
		- 信息隐藏
		- 容易转为ADT

	- 原则

		- 所有代码通过访问器子程序来存储数据
		- 不要把所有的全局数据都仍在一处

			- 类

		- 用锁定控制对全局变量的访问

			- 签入签出
			- 并发操作

				- 开发阶段

		- 在访问器子程序构建一个抽象层

			- 访问器子程序信息量

		- 使所有访问都发生在同一个抽象层

- 降低风险

	- 创建命名规则
	- 为全部全局变量创建一份注释清单
	- 不要用全局变量存放中间结果
	- 不要把所有的数据都放在同一个大对象中到处传递，以说明你没有使用全局变量

*XMind: ZEN - Trial Version*