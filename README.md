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

#
