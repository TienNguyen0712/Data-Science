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
#### `zeros` `ones` `full` `arange` `linspace`   
* Hàm `zeros` giúp tạo ra mảng Python chứa toàn bộ là số "0"   
```Python
np.zeros( [hàng, cột], dtype = 'Kiểu dữ liệu')
```  
   * Nếu không có dtype thì hàm mặc định là kiểu `float64`
* Hàm `ones` giúp tạo ra mảng Python chứa toàn bộ là số "1"
```Python
np.ones( [hàng, cột], dtype = 'Kiểu dữ liệu')
```
 
* 
