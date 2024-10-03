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
          
 
