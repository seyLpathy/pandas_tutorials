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
```python 
g2 = pd.Series({'1969': 7, '1970': [1, 22]},
                 index=['1969', '1970', '1970'])
```

#### read/select data 
similiar with python list item select```

- read/select data 
1. similiar with python list item selection 
2. when iterating over a series,we loop over the values of the series
3. using iteritems to iterate index and values at the same time 
```python
    for item in george_dupe.iteritems():
        print(item)
```

#### updating data 
1. standard index assignment operations works and performs the update in-place or add a new index
2. if you do index operation via assignment operations to an existing index entry will overwrite previous entries
3. perform an index assignment of the .iloc atrribute
```python
george_dupe.iloc[3] = 22   # base on position to access the entries

```
4. `.append` methods of series return a new series that appended and keep the origin series intact
```python 
george_dupe.append(pd.Series({'1974':9}))
george_dupe.set_value('1974', 9) # add a new item to the existing series and return a series

```
#### deletion 
- base on index , `del geroge_dupe['1973']`
- boolean array `george_dupe[george_dupe <= 2]`

### series indexing
1. `george.index.is_unique` returns whether its index has duplicated indexes
2. **even a series with non-numeric indexes,you can also access a series's item by position**
3. if one series uses integer lables, position based indexing won't work 
4. optimized data access methods `.iloc` and `.loc`,the first one index by position ,which also support slicing like python list 
the second is based on the index labels not the positions.
5. `.at` and `.iat` are similiar to `.loc` and `.iloc`.but return a numpy.ndarry
6. slicing series can be acquired by methods mentioned above
7. boolean Arrays can be also used in slicing series,other broadcasting operations to a series is plausible too

### series Methods
in general,the methods return a new series object
- .keys() return index 
#### methods
- get(label,[default]) return a scalar for label or default on failed lookup
- get_value(label) return a scalar for label
- .indexlabels can also access to the specfic item
- .reset_index will return a ** dataframe ** not a series 
``` python 
songs_66.reset_index(drop=True) # remove the index columns 

songs_66.reindex(['Billy', 'Eric', 'George', 'Yoko']) # change the series's index content

songs_66.rename({'Ringo':'Richard'}) # rename can use dict mapping or function that return new index labels
songs_66.rename(lambda x: x.lower())
```
---
- `.count` returns the number of non-null items
- values_counts() returns a mapping of those values to their counts,ordered by frequency
- `unique` and `nunique` which return unique values ,array
- `.drop_duplicates()` remove duplicate 
---
- statistics
1. sum()
2. mean()
3. quantile()
4. describe()
5. var()
6. min()/idmin()
7. skew()
---
- Nan related
1. `.clip` and  `.round` both do not change the data type 
2. `.astype` convert values to the typed pass in 
- to_* functions does not work well in this part
- dealing with none 
3. `.fillna(default) dropna() .notnull()` return boolean array that inspect the nan values


