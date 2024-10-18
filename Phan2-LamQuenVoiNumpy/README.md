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
* Dùng `Tên mảng[index giá trị cần tiếp cận ]` để tiếp cận giá trị mình muốn
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
* Dùng `.T` để chuyện vị cho ma trận
```Python
Tên mảng.T
```
### Nổi những Mảng Numpy và Chia nhỏ Mảng Numpy
* Dùng `concatenate` để nối những mảng khác nhau với nhau
```Python
np.concatenate((Tên mảng muốn nối thứ 1, Tên mảng muốn nối thứ 2), axis = 0/1)
# axis = 1 : Nối theo cột
  axis = 0 : Nối theo hàng ( Mặc định )
```
* Dùng `np.vstack((Tên mảng 1, Tên mảng 2))` giúp nối các Mảng theo cột với nhau
* Dùng `np.hstack((Tên mảng 1, Tên mảng 2))` giúp nối các Mảng theo hàng với nhau
* Dùng `split` để tách chia nhỏ Mảng
```Python
no.split(Tên mảng muốn chia, [Ví trí bắt đầu muốn chia, Ví trí kết thúc chia])
```
### Thực hiện các phép tính trên các Mảng Numpy có kích thước khác nhau 
