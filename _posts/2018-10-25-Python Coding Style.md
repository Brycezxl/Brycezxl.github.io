---
title: Python代码风格规范
categories:
 - 新手村
tags:
 - 新手村
---

#### 总结了易忽略的几个点。

[Google开源项目风格指南](https://zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/python_style_rules/#id1)

<br />

<!--more-->
1. 每行不超过80个字符(例外:长的导入模块语句,注释里的URL)
2. 当’=’用于指示关键字参数或默认参数值时, 不要在其两侧使用空格
3. 每节应该以一个标题行开始. 标题行以冒号结尾. 除标题行外, 节的其他内容应被缩进2个空格
   
   **Args**:
   列出每个参数的名字, 并在名字后使用一个冒号和一个空格, 分隔对该参数的描述.如果描述太长超过了单行80字符,使用2或者4个空格的悬挂缩进(与文件其他部分保持一致). 描述应该包括所需的类型和含义. 如果一个函数接受`*foo`(可变长度参数列表)或者`**bar` (任意关键字参数), 应该详细列出`*foo`和`**bar`
   
   **Returns**: (或者 Yields: 用于生成器)
   描述返回值的类型和语义. 如果函数返回None, 这一部分可以省略
   
   **Raises**:
   列出与接口有关的所有异常
4. 类应该在其定义下有一个用于描述该类的文档字符串. 如果你的类有公共属性(Attributes), 那么文档中应该有一个属性(Attributes)段. 并且应该遵守和函数参数相同的格式
5. 如果一个类不继承自其它类, 就显式的从object继承. 嵌套类也一样.
6. 在文件和sockets结束时, 显式的关闭它.推荐使用“with”语句以管理文件:`with open(file) as name`
7. 为临时代码使用TODO注释 `TODO(email or name).....`
8. 导入总应该放在文件顶部, 位于模块注释和文档字符串之后, 模块全局变量和常量之前。顺序：标准库导入,第三方库导入,应用程序指定导入
9. 命名：ExceptionName, ClassName， GLOBAL_VAR_NAME, module_name, package_name, method_name, function_name, instance_var_name, function_parameter_name, local_var_name

***
