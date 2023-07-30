# data structure 数据结构
- series 表示数据的其中一列，观测对象的某一属性
- DataFrame 表示一张包含行与列的数据表
- Panel 表示一组数据表    #使用较少
panel >> DataFrame >> series
## series

### basic syntax
- definition: a series is used to model one dimension of Data
- the index abstraction 任何数据类型据可以作为索引列,   pandas中大部分操作均基于index实现
- creation of a series
---

``` python 
import pandas as pd 
songs = pd.Series([145,23,48,13]),  # 利用列表可轻易生成Series
    name='count')
songs.index    # 访问series的索引列

1. 最左边一列为index列，右列即为名为name的列
2. The object data type is used for strings
```
---
- NaN value (which means Not A Number),只有浮点类型支持NaN,同时进行运算时自动忽略NaN
- 利用布尔值构成的series型数列可以用于过滤series,
`songs[mask]` mask由布尔值构成

### Series CRUD (create/read/update/delete)
- create from python dictionary

