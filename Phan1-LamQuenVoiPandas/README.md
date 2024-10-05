### Làm quen với thư viện Pandas
## Bước 1: Khai báo thư viện
- Khai báo thư viện Pandas bằng câu lệnh Import Pandas as pd
- Khai báo thư viện Numpy bằng câu lệnh Import Numpy as np
## Bước 2: Khai báo bảng dữ liệu (DataSet)
**Lưu ý đuôi của file có thể là csv, excel, tsv**   
**Điều kiện chọn lọc là 1 cột 1 dòng có thể là \n: xuống dòng, hoặc \t: khoảng trắng**
- Khai báo bảng dữ liệu bằng câu lệnh df = pd.read_csv("nguồn/tên_file_đuôi của file" sep = "điều kiện để chọn lọc là 1 cột 1 hàng") //Gắn biến df
- In ra Bảng dữ liệu bằng câu lệnh df.head("Số hàng muốn in")
## Bước 3: Có cái nhìn tổng quát trong bảng dữ liệu 
- Dùng câu lệnh df.shape() để in ra có bao nhiêu hàng bao nhiêu cột trong bảng dữ liệu
- Dùng câu lệnh df.describe() để in ra các giá trị lớn, nhỏ, trung bình
- **Lưu ý không dùng describe() với các giá trị thuộc kiểu dữ liệu là xâu chuỗi**
- Dùng câu lệnh df.info() để ỉn ra các thông tin như kiểu dữ liệu, số dữ liệu của từng cột trong bảng dữ liệu
- Để biết xâu hơn về bao nhiêu cột có trong bảng dữ liệu, dùng câu lệnh: df.columns
- Để biết rằng dữ liệu trong bảng dũ liệu sẽ xuất hiện từ index nào dùng câu lệnh: df.index
### Các câu lệnh khác: 
#### loc và iloc
- loc là viết tắt của located tức là vị trí câu lệnh loc cho phép lấy dữ liệu từ các cột mong muốn 
trong bảng dữ liệu:
```Python
Vd: df.loc[(df.quantity == 15) | (df.item_name == "Nantucket Nectar")]
```   
            Nhằm lấy cột "quantity" có giá trị nào băng 15
            hoặc lấy cột "item_name" có tên gọi bằng "Nantucket Nectar"
  
  => Vậy sẽ lấy cột "quality" bằng 15 hoặc lấy cột "item_name" bằng "Nantucket Nectar" hoặc cột có cả hai giá trị trên
```Python  
Vd: df.loc[(df.quantity == 2) & (df.item_name == "Nantucket Nectar"), ['order_id', 'quantity', 'item_name']]
```
          Nhằm lấy cột "quantity" có giá trị nào bằng 2
          và lấy cột "item_name" có giá trị là "Nantucket Nectar"
          trong đó từ bảng dữ liệu chỉ lấy ra 3 cột là "order_id" , "quantity", "item_name"

  => Vậy sẽ lấy cột "quantity" có giá trị bằng 2 và lấy cột "item_name" có giá trị là "Nantucket Nectar" trong bàng dữ liệu chỉ lấy ra 3 cột là "order_id" , "quantity", "item_name"
  - Khác với loc thì iloc giúp lấy các hàng có index = n
    Cú pháp :
    ```Python
                df.iloc[hàng có index muốn láy]   
                ##Ví dụ là 10 thì sẽ lấy hàng thứ 9
    ```
    -Câu lệnh trên nhằm lấy trong bảng dữ liệu hàng có số n thì sẽ lấy hàng thứ n - 1
    -Chỉ in ra theo kiểu "series" 
    -Muốn in ra theo hàng trên bảng dữ liệu thì thêm dấu "[]" vào trong "hàng có index muốn lấy" 
    -Ngoài ra còn có thể dùng câu lệnh "iloc" để lấy hàng bắt đầu cũng như kết thúc **Dựa vào index**
    ```Pyhton

               df.iloc[index bắt đầu : index kết thúc]
    ```
    -Ngoài ra "iloc" còn quan trọng trong việc lấy các cột tùy ý và có thể hữu dụng cho việc dự đoán cũng như phân tích
    ```Python

                df.iloc[index bắt đầu : index kết thúc, :-1]    
                ##In các hàng từ index bắt đầu nhưng bỏ cột cuối : tức từ cột index = 0 đến cột cuối
    ```
    -Nếu xây dựng các model cho bài toán ta có thể gắn biến x cho câu lệnh trên và biến y cho câu lệnh lấy hàng cuối cùng
    ```Python
                df.iloc[index bắt đầu : index kết thúc, -1] ##Câu lệnh lấy cột cuối
    ```
#### Apply()
- Câu lệnh Apply sử dụng nhằm mục đích áp dụng chức năng cho từng cột từng dòng
```Python
          Vd: df.item_price.apply(lambda x : x.replace('$', ''))
  ```
          Lệnh trên nhằm lấy cột item_price dùng lệnh apply() tức áp dụng cho tất cả cá hàng   
          trong cột "item_price" "lamda" : là lệnh nhật các đầu vào trong trường hợp trên là các    
          hàng của cột item_price lệnh "replace" nhăm thay thế "$" thành ''
  => Vậy câu lệnh trên nghĩa chọn cột "item_price" dùng apply() ấp dụng cho tất cả cá hàng của cột bằng cách lưu vào biến lamda thay thế toàn bộ dấu "$" thành ''
  **Lưu ý phải đổi kiểu dữ liệu trong trường hợp trên có thể viết**
  ```Python
  df.item_price.apply(lambda x : float(x.replace('$', '')))
  ```
  **Lệnh float nhằm chuyển kiểu dữ liệu từ Objext sang thành Float**
  **Lưu ý kế tiếp lệnh apply() chỉ áp dụng tạm thời cho dòng câu lệnh nếu muốn lưu hoàn toàn thì phải gán ngược lại với giá trị được lưu**
  ```Python
  df.item_price = df.item_price.apply(lambda x : float(x.replace('$', '')))
  ```
  *Lưu toàn bộ cột "item_price" trong bảng dữ liệu theo câu lệnh Apply()*   
  
Để kiểm tra kiểu dữ liệu của toàn bộ dữ liệu trong bảng dữ liệu : 
- Dùng câu lệnh dtype()
  ***Lưu ý khi dùng câu lệnh dtype***
```Code
'b'       boolean
'i'       (signed) integer
'u'       unsigned integer
'f'       floating-point
'c'       complex-floating point
'O'       (Python) objects
'S', 'a'  (byte-)string
'U'       Unicode
'V'       raw data (void)
```
#### Tạo một cột mới 
-Ví dụ muốn tạo thêm một cột "total_price" bằng tích của  "item_price" và "quantity"
```Python
            df["total_price"] = df["item_price"]*df["quantity"]
```
Ví dụ muốn biết tổng toàn bộ doanh thu
```Python
            revenue = df["total_price"].sum()
            print(revenue)
```
#### Xác định xem vật nào xuất hiện nhiều nhất trong bảng dữ liệu ####
#### Group By ####
Lệnh Group By dùng khi muốn gộp các bảng dữ liệu nhỏ theo các tên của các cột để biết được có bao nhiêu   
lần xuất hiện của dữ liệu có trong bảng 
```Python

            df.groupby("item_name") 
            #Hàm trên chỉ trả lại thông báo đã tạo ra một bảng dữ liệu mới chứ không tả lại giá trị
            df.groupby("item_name").apply(print)
            #Đê cho bảng dược xuất hiện sử dụng câu lệnh Apply(print nhằm dán các tác động lên từng   
            hàng của cột "item_name
```
Tuy nhiên ở đây ta chỉ quan tâm số lượng của theo cột "item_name" tức "quantity" do đó ta cần thêm dấu "[]"  
để chỉ in ra cột "quantity"
```Python
            df.groupby("item_name")["quantiy"].apply(print)
                        #Câu lệnh trên đặt cột "quantity" vào dấu ngoặc vuông nhằm chỉ lấy cột "quantity"
                        ứng với cột "item_name" và in ra ngoài màn hình
```
Để cộng lại ta dùng hàm **sum()**
```Python
            df.groupby("item_name")["quantity].sum()
                        #Câu lệnh trên sẽ in ra "quantity" của từng item ứng với "item_name" khác nhau có trong băng
```
Để sắp xếp giá trị tăng hay giảm dần ta dùng hàm **sort_values()**
```Python
            c = df.groupby("item_name")["quantity].sum()             #Câu lệnh trên nhằm gán biến c cho tổng của các item
            c.sort_values()             #Câu lệnh này rắp xếp các gia trí, dữ liệu của bảng
```
#### Lưu ý: Nếu sắp xếp giảm dần thì cho "sort_values(ascending = false)" mặc định của "sort_values" là tăng dần
-Dùng hàm head() để in ra top món hàng cao nhất mà bạn mong muốn 
#### Unique Values: Hay là dữ liệu không trung lặp ( Dữ liệu khác nhau )
-Dùng hàm **values_counts()** để đếm số lần giá trị khác nhau xuất hiện trong bảng theo một giá trị nào đó
```Python
            df.item_name.values_counts()  
                        #Giống với hàm groupby() hàm values_counts() giúp tính những món hàng
            khác nhau trong cột "item_name"
```
-Dùng thêm một hàm **counts()** để đếm xem tông cộng bao nhiêu món hàng được đếm ra
-Ngoài ra, trong Pandas còn có hàm chuyên dùng để tính những giá trị khác nhau có trong bảng chính là hàm **nunique()**
```Python
            df.item_name.nunique()
                        #Vân in ra giá trị giống với khi xài "  df.item_name.values_counts().count()"
```
### Đó là những thao tác quan trọng trong việc thao tác trên bảng dữ liệu và tìm kiếm thông tin mà mình muốn   
### Để có thể đến các bước tiếp theo nhằm xây dựng các module máy học, thực hiện thuật toán, hay dự đoán
            
