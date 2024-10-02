### Làm quen với thư viện Pandas
## Bước 1: Khai báo thư viện
- Khai báo thư viện Pandas bằng câu lệnh Import Pandas as pd
- Khai báo thư viện Numpy bằng câu lệnh Import Numpy as np
## Bước 2: Khai báo bảng dữ liệu (DataSet)
**Lưu ý đuôi của file có thể là csv, excel, tsv.**
**Điều kiện chọn lọc là 1 cột 1 dòng có thể là \n: xuống dòng, hoặc \t: khoảng trắng**
- Khai báo bảng dữ liệu bằng câu lệnh df = pd.read_csv("nguồn/tên_file_đuôi của file" sep = "điều kiện để chọn lọc là 1 cột 1 hàng") //Gắn biến df
- In ra Bảng dữ liệu bằng câu lệnh df.head("Số hàng muốn in")
## Bước 3: Có cái nhìn tổng quát trong bảng dữ liệu 
- Dùng câu lệnh df.info() để in ra có bao nhiêu hàng bao nhiêu cột trong bảng dữ liệu
- Dùng câu lệnh df.describe() để in ra các giá trị lớn, nhỏ, trung bình
- **Lưu ý không dùng describe() với các giá trị thuộc kiểu dữ liệu là xâu chuôi**
- 
