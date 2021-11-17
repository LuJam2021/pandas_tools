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
```python
