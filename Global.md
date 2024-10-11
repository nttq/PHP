Trong PHP, từ khóa `global` được sử dụng để truy cập các biến toàn cục (global variables) bên trong một hàm. Mặc định, các biến khai báo bên ngoài hàm (toàn cục) không thể truy cập trực tiếp từ bên trong hàm, do phạm vi của biến trong PHP bị giới hạn. Để sử dụng các biến toàn cục trong hàm, bạn phải khai báo chúng với từ khóa `global`.

### 1. **Cách sử dụng từ khóa `global`**

Khi bạn khai báo một biến toàn cục với từ khóa `global` bên trong hàm, PHP sẽ tìm biến có cùng tên bên ngoài hàm và sử dụng nó.

#### Ví dụ:

```php
<?php
$a = 10;
$b = 20;

function sum() {
    global $a, $b; // Khai báo sử dụng biến toàn cục $a và $b
    $b = $a + $b;
}

sum();
echo $b; // Kết quả: 30
?>
```

Trong ví dụ này, biến `$a` và `$b` được khai báo ở ngoài hàm, nhưng bên trong hàm `sum()`, chúng ta có thể truy cập và thay đổi giá trị của chúng nhờ từ khóa `global`.

### 2. **Sử dụng biến toàn cục mà không cần `global`**

Ngoài cách sử dụng từ khóa `global`, bạn có thể truy cập biến toàn cục thông qua mảng siêu toàn cục `$GLOBALS`. Đây là một mảng liên kết trong PHP, chứa tất cả các biến toàn cục.

#### Ví dụ sử dụng `$GLOBALS`:

```php
<?php
$a = 10;
$b = 20;

function sum() {
    $GLOBALS['b'] = $GLOBALS['a'] + $GLOBALS['b']; // Sử dụng mảng $GLOBALS để truy cập biến toàn cục
}

sum();
echo $b; // Kết quả: 30
?>
```

Trong ví dụ này, mảng `$GLOBALS` cho phép chúng ta truy cập biến toàn cục `$a` và `$b` từ bên trong hàm mà không cần dùng từ khóa `global`.

### 3. **Lưu ý khi sử dụng `global`**

- Sử dụng quá nhiều biến toàn cục có thể khiến mã của bạn khó theo dõi và bảo trì.
- Nếu có thể, hạn chế sử dụng biến toàn cục và thay vào đó sử dụng các tham số hàm và giá trị trả về để truyền dữ liệu giữa các hàm.

### 4. **Tóm tắt**

- Từ khóa `global` được dùng để truy cập các biến toàn cục bên trong hàm.
- Mảng siêu toàn cục `$GLOBALS` là một cách khác để truy cập biến toàn cục mà không cần dùng từ khóa `global`.
- Hạn chế sử dụng biến toàn cục để tránh các vấn đề về quản lý và bảo trì mã.
