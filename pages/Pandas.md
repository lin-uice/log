- series 本质是numpy一元数组,如下表,按照表的含义改写即可(有点数据库的味道
	- |index|values|
	  |--|--|
	  |0|1|
	  |1|2|
	  |2|3|
	- 法1
		- ```python
		  data=pd.Series([1,2,3,4,5],index=['one','tow','three','four','five'])
		  ```
	- 法2
		- ```python
		  population_dict={'bj':3000,'gz':1500,'sh':'2800'}
		  population_series=pd.Series(population_dict)
		  ```
	- 法3  可以用index刪除一部分行
		- ```python
		  company={1:"Google",2:'Runoob',3:'Wiki'}
		  s_company=pd.Series(company,index=[1,2])
		  s_company
		  ```
	- 法4
- DataFrame
	- 本质  横向的延伸
		- |index|site|age|
		  |--|--|--|
		  |0|Google|10|
		  |1|Runnoob|12|
	- 法1
		- ```python
		  c=[['Google',10],['Runoob',12]]
		  city=pd.DataFrame(c,columns=["site","age"])
		  city
		  ```
		- |  | site | age |
		  | -- | -- | ---|
		  | 0 | Google | 10 |
		  | 1 | Runoob | 12 |
	- 法2
		- ```python
		  d=[['Google','Runoob'],[10,12]]
		  # e={'city':d[0],'age':d[1]}
		  # city=pd.DataFrame(e)
		  # e1=pd.Series(d[0])
		  # e2=pd.Series(d[1])
		  
		  city=pd.DataFrame({'city':d[0],'age':d[1]})
		  city
		  ```
		- |index| city | age |
		  | -- | ---| -- |
		  | 0 | Google | 10 |
		  | 1 | Runoob | 12 |
	- 法3
		- ```python
		  population_dict={'beijing':3000,'shanghai':1200,'guangzhou':1800}
		  area_dict={'beijing':300,'guangzhou':200,'shanghai':180}
		  population_series=pd.Series(population_dict)
		  area_series=pd.Series(area_dict)
		  city=pd.DataFrame({'area':area_series,'population':population_series})
		  city
		  ```
		- |          | area |population|
		  | -- | -- | -- |
		  | beijing | 300 | 3000 |
		  | guangzhou | 200 | 1800 |
		  | shanghai | 180 | 1200 |
	- 法4
		- ```python
		  a={'a':1,'b':2}
		  b={'a':2,'b':3,'c':4}
		  c=pd.DataFrame([a,b])
		  c
		  ```
		- |   | a | b | c |
		  | -- | -- | -- |
		  | 0 | 1 | 2 | NaN |
		  | 1 | 2 | 3 | 4.0 |
	- 注意
- 类似于数据库操作
	- iloc   对数字取,类似于二维数组
	- loc   对'a','b'等取
	- 进行数据处理
		- 对空元素
			- ```python
			  print(data)
			  data.fillna(method='ffill')
			  ```
			- ```python
			  for i in data.columns:
			      data[i]=data[i].fillna(np.nanmean(data[i]))
			  data
			  ```
		- 拼接  concat,以及merge
		- 进行数据筛选
			- ```python
			  a
			  print(a[a>a.mean()])
			  print(data[a>a.mean()])
			  print(data[a>a.mean()].loc[:,['a','b']])
			  ```
			-
-
-