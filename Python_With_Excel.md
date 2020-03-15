# 需要事先需要用pip install命令安装的模块
* pandas
* openpyxl
* xlrd
* numpy

```python
import pandas as pd 
import numpy as np
from openpyxl.workbook import Workbook
```

# 操作Excel和txt文件
```python
df_excel = pd.read_excel('regions.xlsx')          #读取EXCEL文件  用print(df_excel)来输出内容

df_txt = pd.read_csv('data.txt', delimiter='\t')  #读取TXT文件，并以制表符TAB作为分隔符
```

# 操作CSV文件
编号|内容|方法
---|:---:|---:
001| 读取CSV文件| pandas.read_csv
002| 转换保存成Excel文件| df_csv.to_excel('Modified.xlsx')
003| 为column设定header| df_csv.columns = ['First', 'Last']
004| 进行纵向数据提取数据和切片| print(df_csv['State'][0:3]) 
005| 提取需要的header下的数据| print(df_csv[['State', 'Area Code']])
006| 横向对index为1的数据进行读取。| print(df_csv.iloc[1]) 
007| 对横向index为2，纵向顺序为1的数进行提取| print(df_csv.iloc[2, 1])
008| 提取City为Riverside的信息| print(df_csv.loc[df_csv['City'] == 'Riverside'])
009| 同时匹配两对Key和value，找到所需信息| print(df_csv.loc[(df_csv['City'] == 'Riverside') & (df_csv['First'] == 'John')])
010| 新增一个一个名为"Tax %"的column，并指明计算tax的方法| df_csv['Tax %'] = df_csv['Income'].apply(lambda x: .15 if 10000 < x < 40000 else .2 if 40000 < x <80000 else .25)
011| 使用drop来把几个不要的纵列剔除出去显示| df_csv.drop(columns='Address', inplace=True)
012| 添加一个判断真伪的纵列| df_csv['Col Test'] = False + df_csv.loc[df_csv['Income'] < 60000, 'Col Test'] = True
013| 使用groupby()[Link!](https://blog.csdn.net/FrankieHello/article/details/97272990)|df_csv.groupby(['Col Test'])
014| 使用set_index来手动设置index| set_index('Area Code')
015| 使用str.split(expand=True)做数据分割| df.First.str.split(expand=True)
016| 用numpy将NaN换成N/A.| df.replace(np.nan, 'N/A', regex=True)

```python
df_csv = pd.read_csv('Names.csv', header=None)     #001 读取CSV文件

df_csv.to_excel('Modified.xlsx')                   #002 转换保存成Excel文件

df_csv.columns = ['First', 'Last', 'Address', 'City', 'State', 'Area Code', 'New ID']  #003 为上述CSV文件添加headers

print(df_csv.columns)
#結果：Index(['First', 'Last', 'Address', 'City', 'State', 'Area Code', 'New ID'], dtype='object')

print(df_csv)    #添加了header后的csv显示
#结果：
                 First      Last                           Address         City State  Area Code  New ID
0                 John       Doe                 120 jefferson st.    Riverside    NJ       8074   45000
1                 Jack  McGinnis                      220 hobo Av.        Phila    PA       9119   18000
2        John "Da Man"    Repici                 120 Jefferson St.    Riverside    NJ       8075  120000
3              Stephen     Tyler  7452 Terrace "At the Plaza" road     SomeTown    SD      91234   90000
4                  NaN  Blankman                               NaN     SomeTown    SD        298   30000
5  Joan "Danger", Anne       Jet               9th, at Terrace plc  Desert City    CO        123   68000

print(df_csv['State'][0:3])        #004 进行纵向数据提取数据和切片
#结果
0     NJ
1     PA
2     NJ
Name: State, dtype: object

print(df_csv[['State', 'Area Code']])  #005 提取需要的header下的数据
#结果
  State  Area Code
0    NJ       8074
1    PA       9119
2    NJ       8075
3    SD      91234
4    SD        298
5    CO        123

print(df_csv.iloc[1])               #006 横向对index为1的数据进行读取。
#结果
First                Jack
Last             McGinnis
Address      220 hobo Av.
City                Phila
State                  PA
Area Code            9119
New ID              18000
Name: 1, dtype: object

print(df_csv.iloc[2, 1])            #007 对横向index为2，纵向顺序为1的数进行提取
结果：Repici

#用以下方法可以将自己需要的column，以自己需要的文件名，没有index地保存成一个Excel文件。运行完成查看一下目录。
wanted_values = df_csv[['First', 'Last', 'State']]
stored = wanted_values.to_excel('Saving_file.xlsx', index=None)


print(df_csv.loc[df_csv['City'] == 'Riverside'])      #008 提取city为Riverside的信息
#结果
           First    Last            Address       City State  Area Code  New ID
0           John     Doe  120 jefferson st.  Riverside    NJ       8074   45000
2  John "Da Man"  Repici  120 Jefferson St.  Riverside    NJ       8075  120000

print(df_csv.loc[(df_csv['City'] == 'Riverside') & (df_csv['First'] == 'John')])  #009 同时匹配两对Key和value，找到所需信息
#结果
  First Last            Address       City State  Area Code  New ID
0  John  Doe  120 jefferson st.  Riverside    NJ       8074   45000

#010 用以下方法新增一个一个名为"Tax %"的column，并指明计算tax的方法
df_csv.columns = ['First', 'Last', 'Address', 'City', 'State', 'Area Code', 'Income']
df_csv['Tax %'] = df_csv['Income'].apply(lambda x: .15 if 10000 < x < 40000 else .2 if 40000 < x <80000 else .25)
print(df_csv)
#结果
                 First      Last                           Address         City State  Area Code  Income  Tax %
0                 John       Doe                 120 jefferson st.    Riverside    NJ       8074   45000   0.20
1                 Jack  McGinnis                      220 hobo Av.        Phila    PA       9119   18000   0.15
2        John "Da Man"    Repici                 120 Jefferson St.    Riverside    NJ       8075  120000   0.25
3              Stephen     Tyler  7452 Terrace "At the Plaza" road     SomeTown    SD      91234   90000   0.25
4                  NaN  Blankman                               NaN     SomeTown    SD        298   30000   0.15
5  Joan "Danger", Anne       Jet               9th, at Terrace plc  Desert City    CO        123   68000   0.20

#011 接上，再添加一个'Tax Owed'的纵列，然后使用drop来把几个不要的纵列剔除出去显示
df_csv['Tax Owed'] = df_csv['Income'] * df_csv['Tax %']
to_drop = ['First', 'Address', 'City', 'State', 'Area Code']
df_csv.drop(columns=to_drop, inplace=True)
print(df_csv)
#结果：
       Last  Income  Tax %  Tax Owed
0       Doe   45000   0.20    9000.0
1  McGinnis   18000   0.15    2700.0
2    Repici  120000   0.25   30000.0
3     Tyler   90000   0.25   22500.0
4  Blankman   30000   0.15    4500.0
5       Jet   68000   0.20   13600.0

#012 接上，添加一个判断真伪的'Col Test'纵列
df_csv['Col Test'] = False
df_csv.loc[df_csv['Income'] < 60000, 'Col Test'] = True
print(df_csv)
#结果：
       Last  Income  Tax %  Tax Owed  Col Test
0       Doe   45000   0.20    9000.0     False
1  McGinnis   18000   0.15    2700.0     False
2    Repici  120000   0.25   30000.0      True
3     Tyler   90000   0.25   22500.0      True
4  Blankman   30000   0.15    4500.0     False
5       Jet   68000   0.20   13600.0      True

#013 接上。使用groupby()分组。
print(df_csv.groupby(['Col Test']).mean().sort_values('Income'))
结果：
                Income     Tax %      Tax Owed
Col Test
True      31000.000000  0.166667   5400.000000
False     92666.666667  0.233333  22033.333333

print(type(df_csv.groupby(['Col Test'])))
结果：<class 'pandas.core.groupby.generic.DataFrameGroupBy'>

# 014 以下，先把'Address'这个column扔出去，然后打印出'Area Code'为8074的信息。
df_csv.drop(columns='Address', inplace=True)
df = df_csv.set_index('Area Code')
print(df.loc[8074])
结果：
First          John
Last            Doe
City      Riverside
State            NJ
Income        45000
Name: 8074, dtype: object

#print(df.iloc[0])这个的输出可上面是一样的。


print(df.loc[91234: , 'First'])
结果：
Area Code
91234                Stephen
298                      NaN
123      Joan "Danger", Anne
Name: First, dtype: object


#015 接上。使用str.split(expand=True)做数据分割。
df = df_csv.set_index('Area Code')
print(df.First.str.split(expand=True))
结果：
                 0          1     2
Area Code
8074          John       None  None
9119          Jack       None  None
8075          John        "Da  Man"
91234      Stephen       None  None
298            NaN        NaN   NaN
123           Joan  "Danger",  Anne


df = df_csv.set_index('Area Code')
df.First = df.First.str.split(expand=True)
print(df)
结果：
             First      Last         City State  Income
Area Code
8074          John       Doe    Riverside    NJ   45000
9119          Jack  McGinnis        Phila    PA   18000
8075          John    Repici    Riverside    NJ  120000
91234      Stephen     Tyler     SomeTown    SD   90000
298            NaN  Blankman     SomeTown    SD   30000
123           Joan       Jet  Desert City    CO   68000

#016 接上。用numpy将NaN换成N/A.
df = df.replace(np.nan, 'N/A', regex=True)
print(df)
结果：
             First      Last         City State  Income
Area Code
8074          John       Doe    Riverside    NJ   45000
9119          Jack  McGinnis        Phila    PA   18000
8075          John    Repici    Riverside    NJ  120000
91234      Stephen     Tyler     SomeTown    SD   90000
298            N/A  Blankman     SomeTown    SD   30000
123           Joan       Jet  Desert City    CO   68000
```

# openpyxl
首先不要忘记导入模块。
```python
from openpyxl.workbook import Workbook
from openpyxl import load_workbook
```
编号| 内容| 方法
---|---|---
1000| 创建新的sheet，并指定顺序|  create_sheet('NewSheet1', 0)
1001| 导入一个excel|  load_workbook('regions.xlsx')
1002| 替换一个cell的值| active_sheet['A1'] = 'New_value'
1003| 保存更改为一个新的Excel| wb2.save('New_regions.xlsx')

```python
from openpyxl import load_workbook

wb = Workbook()
ws = wb.active

ws1 = wb.create_sheet('NewSheet')
ws2 = wb.create_sheet('NewSheet1', 0)     #1000 创建一个新的sheet，并指定顺序

ws.title = 'MySheet'

print(wb.sheetnames)    #结果：['NewSheet1', 'MySheet', 'NewSheet']
```
```python
wb2 = load_workbook('regions.xlsx')   #1001 导入一个excel

new_sheet = wb2.create_sheet('NewNewSheet')   #创建一个新的sheet

active_sheet = wb2.active

cell = active_sheet['A1']

print(cell)
print(cell.value)

active_sheet['A1'] = 'New_value'      #1002 替换一个cell的值
print(cell.value)

wb2.save('New_regions.xlsx')          #1003 保存更改为一个新的Excel

print(pd.read_excel('New_regions.xlsx'))
```




