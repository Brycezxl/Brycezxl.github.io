---

title: torchtext操作小结
tags:
 - Pytorch
---



<!--more-->

## 创建数据集

创建一个函数来处理数据集



### 定义Field

field用来定义如何处理数据，以及储存vocab等信息

可以定义不同的field处理不同类型字段

最后每种个输入的数据都要对应一个field

```````
from torchtext.data import Field, LabelField

label_field = LabelField(sequential=False, batch_first=True, use_vocab=False)
text_field = Field(batch_first=True)
field = [('text1', text_field), ('text2', text_field), ('label', label_field)]
```````



### 读取数据

首先定义`examples = []`来储存数据

对于每一条数据，按照field中的顺序放在一个list中，并且和field一起加入example里

```
from torchtext.data import Example

examples.append(Example.fromlist(data, field))
```



### 生成数据集

加载完数据以后，创建dataset即可

```
from torchtext.data import Dataset

length = examples.__len__()
train_examples = Dataset(examples[:int(0.8 * length)], field)
test_examples = Dataset(examples[int(0.8 * length):], field)
return train_examples, test_examples
```



## 创建词表

此处生成字段到id的映射， 也可以定义最少出现频次

````
field.build_vocab(train，test)  # test也可不加
````



##　创建迭代器

BuckerIterator可以根据sort key来对数据集内的数据进行排序，长度相似的一起训练，加快训练速度

````
train_iter, test_iter = BucketIterator.splits(
        (train, test),
        batch_sizes=(64, 64),
        device=device,
        sort_key=len(x.text1),
        repeat=False,
        )
````



然后就可以开心训练了！



### 制定不同目标

* 短期：月
* 中期：年
* 长期：5年以上



### 目标评判原则 SMART

* S :   Specific, 制定的目标要具体，例如买一辆多少钱的车，全款还是贷款，首付多少
* M:   Measurable, 目标要容易衡量
* A :   Attainable, 可行的
* R :   Realistic, 现实
* T :   Time, 制定完成期限



## 2. 预算

- 可变的
- 每月回顾现金流，按分类列出所有的支出，找一找哪些是不必要的支出，下月调整
- 找出可变费用，是否可以调整



水课一门，弃了