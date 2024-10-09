
# Làm quen với thư viện Pandas
# Mục lục
- [Khai báo & Biến đổi Dữ liệu](#import-export-data)
- [Bước dầu và Tìm hiểu](#getting-and-knowing)
  - [loc và iloc](#loc-vs-iloc)
  - [Nhận biết Hàng của Bảng Dữ Liệu](#access-columns-of-data-frame)
  - [Nhận biết Cột của Bảng Dữ Liệu](#access-columns-of-data-frame)
- [Chuyển đổi Dữ Liệu](#manipulating-data)
- [Grouping: Gộp](#grouping)
  - [Grouping Cơ bản](#basic-grouping)
  - [Tạo DataFrame từ dữ liệu thô](#creating-dataframe)


# Khai báo và Chuyển đổi dữ liệu
### Khai báo với các kiểu dữ liệu khác nhau
```Python
users = pd.read_csv('user.csv', sep='|')
chipo = pd.read_csv(url, sep = "\t")
```
<img height="500" alt="pandas-anatomy-of-a-dataframe" src="https://user-images.githubusercontent.com/64508435/111490410-f833cd80-8775-11eb-8527-daf08dc8e91a.png">

#### Thay đỏi tên Index
```Python
users = pd.read_csv('u.user', sep='|', index_col='user_id')
```
### Chuyển đổi cũng như khai báo
```Python
users.to_csv("exported-users.csv")
```

# Làm quen và Tìm hiểu
### shape : Trả về (Row, Column): Cột và Hàng
```Python
df = pd.DataFrame({'col1': [1, 2], 'col2': [3, 4],
                   'col3': [5, 6]})
df.shape
(2, 3) # df.shape[0] = 2 row, df.shape[1] = 3 col
```
### info() : Trả về index dtype, columns, non-null values & memory usage.
###                kiễu dữ liệu, cột, giá trị null và chiếm bao nhiêu bộ nhớ
```Python
df.info()
```
-Ta sẽ hiểu kiểu dữ liệu của cột, bao nhiêu giá trị null của bảng dữ liệu
```Python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 4622 entries, 0 to 4621
Data columns (total 5 columns):
 #   Column              Non-Null Count  Dtype 
---  ------              --------------  ----- 
 0   order_id            4622 non-null   int64 
 1   quantity            4622 non-null   int64 
 2   item_name           4622 non-null   object
 3   choice_description  3376 non-null   object
 4   item_price          4622 non-null   object
dtypes: int64(2), object(3)
memory usage: 180.7+ KB
````

### describe() : Phân tích trực quan các dữ liệu có trong bảng
```Python
chipo.describe() #Notice: mặc định chỉ có kiểu dữ liệu số được trả lai 
chipo.describe(include = "all") #Notice: Mặc định, chỉ trả lại kiểu dữ liệu số
```


### dtype : Trả lại kiểu dữ liệu của các dữ liệu trong cột
- `df.col_name.dtype` trả lại kiểu dữ liệu của cột
```Python
df.item_price.dtype
#'O'     (Python) objects
```

- Please note: dtype sẽ trả lại các kiểu dữ liệu với các ký hiệu đặc biệt
```Python
'b'       boolean
'i'       (signed) integer
'u'       unsigned integer
'f'       floating-point
'c'       complex-floating point
'O'       (Python) objects
'S', 'a'  (byte-)string
'U'       Unicode
'V'       raw data (void
```

## loc vs iloc
### loc
- `loc`: is **label-based**, nhằm lấy ra "tên của hàng và cột" mà ta muốn lấy ra.
#### Tìm tất cả các cột hay hàng dựa theo điều kiện
```Python
# Chọn tất cả hàng và cột có số tuổi lớn hơn hoặc bằng 15
data.loc[data.age >= 15]
# Chọn tất cả các cột theo nhiều điều kiện gộp
data.loc[(data.age >= 12) & (data.gender == 'M')]
```
![image](https://user-images.githubusercontent.com/64508435/106067849-7abaec00-613a-11eb-8cbe-f9aa5e2c6202.png)

#### Chỉ lựa chọn 1 cột phù hợp với cột vừa lấy ra từ bảng theo điều kiện 
```Python
# Thay đổi dữ liệu đầu ra dựa theo cột được lấy từ trong bảng dữ liệu
chipo.loc[(chipo.quantity == 7) & (chipo.item_name == 'Bottled Water'), ['item_name', 'item_price']] = ['Tra Xanh', 0]
# Chỉ chọn duy nhất những cột trong dấu "[]" nhằm thỏa điều kiện
chipo.loc[(chipo.quantity > 5), ['item_name', 'quantity', 'item_price']]
```
<img width="381" alt="Screenshot 2021-01-28 at 7 26 04 AM" src="https://user-images.githubusercontent.com/64508435/106067706-32033300-613a-11eb-98ce-114c4c0f9dd6.png">

### iloc
- `iloc`: is **index-based**, cho phép chọn các cột và hàng có index "integer index-based" rằng ta cần lấy ra.
- `.iloc[]` chấp nhận input là:
  #### Chọn hàng
  - An integer, e.g. `dataset.iloc[0]` > return row 0 in `<class 'pandas.core.series.Series'>`
  ```Python
  Country      France
  Age              44
  Salary        72000
  Purchased        No
  ```
  -Danh sách hay mảng số nguyên
  - A list or array of integers, e.g.`dataset.iloc[[0]]` > trả về cột và hàng có index bằng 0 trong Bảng dữ liệu
  ```Python
     Country   Age   Salary  Purchased
  0  France    44.0  72000.0        No
  ```
  -Kiểu Object 
  - A slice object with ints, e.g. `dataset.iloc[:3]` > trả về 3 cột từ index 0 đến 3 và tát cả các cột có trong Bảng dữ liệu 
  ```Python
       Country   Age   Salary Purchased
  0    France   44.0  72000.0        No
  1    Spain    27.0  48000.0       Yes
  2    Germany  30.0  54000.0        No
  ```
  #### Chọn hàng và cột
  - Chọn 3 Hàng đầu tiên và lấy tất cả cột ngoại trừ Cột cuối `X = dataset.iloc[:3, :-1]`
  ```Python
       Country   Age   Salary
  0   France  44.0  72000.0
  1    Spain  27.0  48000.0
  2  Germany  30.0  54000.0
  ```
### Numpy representation of DF
- `DataFrame.values`: Return a Numpy representation of the DataFrame (i.e: Only the values in the DataFrame will be returned, the axes labels will be removed)
- For ex: `X = dataset.iloc[:3, :-1].values`
```Python
[['France' 44.0 72000.0]
 ['Spain' 27.0 48000.0]
 ['Germany' 30.0 54000.0]]
```

## Đếm xem có bao nhiêu cột trong Bảng dữ liệu
### Kiểm tra Index của Bảng dữ liệu
```Python
df.index
#RangeIndex(start=0, stop=4622, step=1)
```

[(Back to top)](#Mục-Lục)

## Kiểm tra cột của bàng dữ liệu
### In ra tên của tất cả các cột của Bảng dữ liệu
```Python
list(df.columns)
#['order_id', 'quantity', 'item_name', 'choice_description','item_price', 'revenue']
```
### Tìm hiểu sâu về cột
```Python
# Đếm xem có bao nhiêu giá trị trong cột
df.col_name.count()
# Lấy mean của giá trị trong cột
df["col_name"].mean()
```
### value_counts() : Trả về danh sách các dữ liệu khác nhau
```Python
index = pd.Index([3, 1, 2, 3, 4, np.nan])
#dropna=False sễ xem np.nan là kiểu dữ liệu khác nhau
index.value_counts(dropna=False)
#Return: 
3.0    2
2.0    1
NaN    1
4.0    1
1.0    1
dtype: int64
```
### Tính tón tổng giá trị khác nhau trong bảng
```Python
#How many unique values : Có bao nhiêu giá trị khác nhau
index.value_counts().count()

index.nunique()
#5
```

[(Back to top)](#Mục-Lục)
# Manipulating Data
## Missing Values: Dữ liệu bị mất
### Thay thế Missing Values với fillna() mà vẫn giữ nguyên số hàng và số cột
- To fill `nan` value with a v
```Python
car_sales_missing["Odometer"].fillna(car_sales_missing["Odometer"].mean(), inplace = True)
```
### Loại bỏ các dữ liệu bị mất với dropna()
- Để loại bỏ các hàng có dữ liệu Missing Values
```Python
car_sales_missing.dropna(inplace=True)
```
## Loại bỏ cột

```Python
car_sales.drop("Passed road safety", axis = 1) # axis = 1 Nếu ta muốn loại bỏ cột
```
[(Back to top)](#Mục-Lục)
# Gộp
<img width="707" alt="Screenshot 2021-01-23 at 10 47 21 PM" src="https://user-images.githubusercontent.com/64508435/105590696-195aec00-5dcd-11eb-894d-3953d6ea8180.png">

## Grouping cơ bản
- Gộp cột "item_name" và lấy tổng giá trị trong cột "quantity"
- Method #1 : `df.groupby("item_name")`

```Python
df.groupby("item_name")["quantity"].sum()
```

```Python
item_name
Chicken Bowl       761
Chicken Burrito    591
Name: quantity, dtype: int64
```

- Method #2: `df.groupby(by=['order_id'])`

```Python
order_revenue = df.groupby(by=["order_id"])["revenue"].sum()
```
## Tạo DataFrame từ dữ liệu Mảng hay thô
```Python
pd.DataFrame(dữ liệu đầu vào, index = [tên hàng 1, tên hàng 2, ...], columns = [tên cột 1, tên cột 2, ...])
```
```Pyhton
import pandas as pd 
pd.DataFrame(sales_amounts, index = ["Mon", "Tues", "Wed ","Thurs", "Fri"],
                                            columns = ["Almond Butter", "Peanut Butter","Cashew Butter"])
``` 
  ![image](https://github.com/TienNguyen0712/Note/blob/main/Screenshot%202024-10-09%20094055.png)

[(Back to top)](#Mục-Lục)
