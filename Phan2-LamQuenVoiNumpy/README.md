## Tìm hiểu về thư viện Numpy
Thư viện Numpy đươc xây dựng dựa trên ngôn ngữ C cung cấp cho ta nhừng hàm phương thức để tương   
tác với các kiểu dữ liệu dạng sô ( Numberic )
* Trong Python kiểu dữ liệu gộp chung chúng thành `List`
    * Bao gồm toàn bộ các kiểu dữ liệu : int, float, str, ... 
### Tạo mảng ở trong thư viện Numpy từ `List Python`
```Python
np.array( Mảng muốn tạo , dtype = 'Kiểu dữ liệu muốn đồng bộ hóa')
```
* Với `List` trong Python có thể lưu trữ các kiểu dữ liệu số khác nhau. Tuy nhiên khi xuất Python sẽ
  tự động chuyển về kiểu dữ liệu mặc định hoặc cao hơn `float64`
* Các thao tác thực hiện với mẩng Numpy
  * `ndim` để xác định số chiều của mảng 
  * `shape` để xác định số hàng và cột của mảng
  * `size` để xác định số thành phần có trong mảng 
### Tạo Numpy Array từ các hàm được xây dựng sẵn
#### `zeros` `ones` `full` `arange` `linspace` `random`
* Hàm `zeros` giúp tạo ra mảng Python chứa toàn bộ là số "0"   
```Python
np.zeros( [hàng, cột], dtype = 'Kiểu dữ liệu') # `float64` là kiểu mặc định
```  
* Hàm `ones` giúp tạo ra mảng Python chứa toàn bộ là số "1"
```Python
np.ones( [hàng, cột], dtype = 'Kiểu dữ liệu') # `float64` là kiểu mặc định
```
* Hàm `arange` giúp tạo mảng Python chứa thành phần là các số ngẫu nhiên
```Python
np.arange( Số bắt đầu, Số kết thúc, Bước nhẩy, dype = 'Kiểu dữ liệu')
```
* Hàm `full` giúp tạo mảng Python lắp đầy dữ liệu nhập từ bàn phím
```Python
np.full( [hàng, cột], Dữ liệu trong mảng, dtype = 'Kiểu dữ liệu')
```
* Hàm `linspace` tạo mảng Python chứa những số tạo ra trong khoảng chia đều
```Python
np.linspace( Số bắt đầu, Số kết thức, Bước chia )
```
* Hàm `random` tạo mảng Python từ các số ngẫu nhiên trong khoảng từ "0" đến "1"
```Python
np.random([hàng, cột])
```
* Hàm `seed` để lưu lại các số ngẫu nhiên
```Python
np.random.seed(Số muốn gán)
```
* Hàm `normal` cho giá trị ngẫu nhiên có giá trị nằm trong giá trị trung bình và độ lệch chuẩn
```Python
np.random.normal( Gía trị trung bình, Độ lệch chuẩn, (Hàng, cột))
```
* Hàm `randint` cho giá trị ngâu nhiên là những con số nguyên nhưng không bao gồm số kết thúc
```Python
np.random.randint( Số bắt đầu, Số kết thúc, (Hàng, Cột)) # type mặc định là int
```
* Ngoài ra còn hàm `rand` cũng giống với `random` nhưng chỉ nhập trực tiếp cột và hàng
```Python
np.random.rand(hàng, cột)
```
### Tiếp cận vị trí giá trị trong Mảng Numpy bằng Index và Cắt mảng
* Dùng `Tên mảng[ index giá trị cần tiếp cận ]` để tiếp cận giá trị mình muốn
* Dùng `Tên mảng[-1]` để tiếp cận giá trị cuối của mảng
* Ngoài ra với các Mảng nhiều chiều cũng có thể tiếp cận bằng cách dùng Index
* Ta cũng có thể dùng Index để thay đổi giá trị với giá trị đã sẵn có trong mảng bằng toán từ gán `=`
* Để cắt mảng ta dùng `Tên mảng[Index bắt đầu: Index cuối: Bước nhảy]`
* Ngoài ra với các mảng đa chiều ta cũng dùng `Tên mảng[:Index muốn cắt/số hàng, :Index kết thúc/Số cột ]`
### Thay đổi dạng của Mảng Numpy và Chuyển vị Ma trận
* Dùng `reshape` để đổi dạng của mảng Numpy
```Python
Tên mảng.reshape((Hàng, Cột))
```
* Dùng `.T` để chuyển vị cho ma trận
```Python
Tên mảng.T
```
### Nổi những Mảng Numpy và Chia nhỏ Mảng Numpy
* Dùng `concatenate` để nối những mảng khác nhau với nhau
```Python
np.concatenate((Tên mảng muốn nối thứ 1, Tên mảng muốn nối thứ 2), axis = 0/1)
# axis = 1 : Nối theo cột
# axis = 0 : Nối theo hàng ( Mặc định )
```
* Dùng `np.vstack((Tên mảng 1, Tên mảng 2))` giúp nối các Mảng theo cột với nhau
* Dùng `np.hstack((Tên mảng 1, Tên mảng 2))` giúp nối các Mảng theo hàng với nhau
* Dùng `np.split` để tách chia nhỏ Mảng
```Python
np.split(Tên mảng muốn chia, [Ví trí bắt đầu muốn chia, Ví trí kết thúc chia])
```
### Thực hiện các phép tính trên các Mảng Numpy có kích thước khác nhau với nhau
* Dùng `Tên mảng + Số bất kỳ` để thực hiện phép cộng cho Mảng
<img width="300" alt="image1" src = "https://github.com/TienNguyen0712/Note/blob/main/broadcasting_1.png">

* Dùng `Tên mảng + Tên mảng` để thực hiện phép cộng cho hai mảng khác nhau
<img width="400" alt="image2" src = "https://github.com/TienNguyen0712/Note/blob/main/broadcasting_2.png">

* Lưu ý không thể thực hiện phép toàn với các Mảng có size lớn hơn
<img width="500" alt="image3" src = "https://github.com/TienNguyen0712/Note/blob/main/broadcasting_3.png">

### Thực hiện các phép toán với các thành phần trong Mảng Numpy ( Nên dùng các hàm trong Numpy vì tốc độ nhanh cũng như tiết kiệm bộ nhớ )    
* Dùng `np.sum()` để tính tổng các thành phần có trong mảng   
   * Hàm `np.sum()` được xây dựng và thực hiện thao tác nhanh hơn hàm `sum()` mà Python có     
   * Dùng `%timeit` để tính toàn thời gian thực hiện 1 câu lệnh trong Python và đăt trước câu lệnh mà ta cần tính     
* Dùng `np.mean()` để lấy giá trị trung bình trong Mảng      
* Dùng `np.max()` để tìm giá trị lớn nhát trong Mảng      
* Dùng `np.min()` để tim giá trị nhỏ nhất trong Mảng     
### Sác xuất thống kê     
#### Standard Deviation: Độ Lệch Chuẩn      
Là kích thước đo độ phân tán của dữ liệu ( So sánh với giá trị trung bình )     
* Dùng `np.std( Tên của Mảng )` để tính độ lệch chuẩn của dữ liệu có trong mảng    
#### Variance: Phương Sai      
Lấy từng điểm dữ liệu một trừ đi cho giá trị trung bình rồi bình phương chính nó lên sau đó làm với những điểm khác rồi tính trung bình của chúng [Xem thêm tại đây](https://www.mathsisfun.com/data/standard-deviation.html)     
Dựa vào phương sai người ta có thể phân loại dữ liệu cũng như đánh giá một cách chính xác và chi tiết hơn
* Dùng `np.var( Tên của Mảng )` để tính phương sai cho dữ liệu có trong Mảng
### Sắp xếp Mảng
* Dùng `np.sort( Tên của Mảng )` để sắp xếp các thành phần trong Mảng theo thuật toán Quick Sort
* Dùng `np.argsort( Tên cảu Mảng )` để trả về Index của các thành phần trước khi hàm `sort()` được gọi
* Ngoài ra còn có thể dùng hàm `sort()` cho các ma trận, hay Mảng đa chiều nhưng phải thêm `axis = 1/0` 1: xếp theo hàng 0: xếp thep cột
### Đại số tuyến tính
