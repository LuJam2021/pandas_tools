```python

# pandas_tools
pandas 常用工具整理

https://www.learncodewithmike.com/2021/03/pandas-data-cleaning.html

dataframe 調色盤
df=.style.backgroung_gradient  

# 刪除 有 "指標" 字串的列
df=df[~df.index.str.contains("指標")]
#str.contains=搜尋

#數值轉型成int
df.columns = df.iloc[0].astype(int)

https://zhuanlan.zhihu.com/p/100064394

  身高 體重  性別 年齡
---------------------
0 160   80   男   18
1 170   70   女   17
2 180   60   男   16
-------Series-------
# map用法
把性別男,女 替換成1,0
```python
#①使用字典进行映射
data["性別"] = data["性別"].map({"男":1, "女":0})

#②使用函数
def gender_map(x):
    gender = 1 if x == "男" else 0
    return gender
#注意这里传入的是函数名，不带括号
data["性別"] = data["性別"].map(gender_map)


# apply用法
年紀偏差值-3
def apply_age(x,bias):
    return x+bias
#以元组的方式传入额外的参数
data["age"] = data["age"].apply(apply_age,args=(-3,))

-------DataFrame-------
# apply用法
沿着0轴求和
data[["height","weight","age"]].apply(np.sum, axis=0)

沿着0轴取对数
data[["height","weight","age"]].apply(np.log, axis=0)

# applymap用法
会对DataFrame中的每个单元格执行指定函数的操作
df = pd.DataFrame(
    {
        "A":np.random.randn(5),
        "B":np.random.randn(5),
        "C":np.random.randn(5),
        "D":np.random.randn(5),
        "E":np.random.randn(5),
    }
)
# 所有直取小數點兩位
df.applymap(lambda x:"%.2f" % x)

# 表格變色
def tableColor(val):
    if val > 20:
        color = 'red'
    elif val < 20:
        color = 'green'
    else:
        color = 'white'
    return 'color: %s' % color
df = df.style.applymap(tableColor, subset=['Close'])
display(df)
```python
