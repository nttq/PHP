Trong PHP, từ khóa `require` được sử dụng để **nhúng nội dung của một file PHP khác** vào file hiện tại. File được nhúng sẽ được tải và thực thi trong ngữ cảnh của file hiện tại. Nếu file được chỉ định không tìm thấy, PHP sẽ tạo ra một **lỗi nghiêm trọng (fatal error)** và ngừng thực thi mã.

### Cú pháp:
```php
require 'path/to/file.php';
```

### Sự khác biệt giữa `require` và `include`:
- **`require`**: Nếu file không tồn tại hoặc không thể nhúng, PHP sẽ dừng chương trình và tạo ra lỗi nghiêm trọng (fatal error).
- **`include`**: Nếu file không tồn tại hoặc không thể nhúng, PHP sẽ tạo ra lỗi cảnh báo (warning) nhưng chương trình sẽ tiếp tục chạy.

Ví dụ:
```php
<?php
require 'header.php'; // Nếu file header.php không tồn tại, PHP sẽ dừng chương trình.

echo "This will not be executed if header.php is missing.";
?>
```

### `require_once`:
- **`require_once`** hoạt động giống `require`, nhưng nó đảm bảo rằng file chỉ được nhúng **một lần duy nhất** trong suốt quá trình thực thi kịch bản. Điều này ngăn chặn việc nhúng cùng một file nhiều lần gây lỗi hoặc hành vi không mong muốn.
  
Ví dụ:
```php
<?php
require_once 'config.php'; // Chỉ nhúng file này một lần, dù được gọi nhiều lần.
require_once 'config.php'; // Lần thứ hai gọi sẽ bị bỏ qua.
?>
```

### Khi nào nên dùng `require`?
- Sử dụng `require` khi file bạn cần là **bắt buộc** để chương trình chạy đúng. Ví dụ: các file chứa cấu hình quan trọng hoặc các thư viện không thể thiếu.
- Sử dụng `require_once` khi bạn muốn chắc chắn rằng file chỉ được nhúng một lần, đặc biệt trong các file có chứa định nghĩa lớp, hàm hoặc cấu hình quan trọng.
------
Trong PHP, **namespace** (không gian tên) là một cách để tổ chức mã và tránh xung đột tên giữa các lớp, hàm, hoặc hằng số khi chúng có cùng tên nhưng được sử dụng trong các tệp hoặc thư viện khác nhau. 
Namespace giúp lập trình viên nhóm các thành phần liên quan lại với nhau và sử dụng chúng dễ dàng hơn.

### Tại sao cần namespace?
- **Tránh xung đột tên**: Nếu bạn sử dụng thư viện bên ngoài hoặc tạo nhiều lớp, hàm với tên giống nhau, namespace giúp tránh xung đột bằng cách định danh chúng trong các không gian tên riêng.
- **Tổ chức mã tốt hơn**: Namespace giúp cấu trúc mã rõ ràng và dễ quản lý, đặc biệt trong các dự án lớn.

### Cách khai báo và sử dụng namespace:

#### 1. Khai báo namespace:
Namespace được khai báo ở đầu file PHP, trước khi có bất kỳ mã PHP nào khác (trừ `declare`):
```php
<?php
namespace MyApp;

class User {
    public function __construct() {
        echo "This is the User class from MyApp namespace.";
    }
}
```

#### 2. Sử dụng namespace:
Khi bạn muốn sử dụng một lớp từ một namespace, bạn cần phải tham chiếu đến nó bằng cách sử dụng tên đầy đủ của namespace hoặc từ khóa `use`.

Ví dụ về khai báo namespace ở các tệp khác nhau:

**File 1: `User.php`**
```php
<?php
namespace MyApp;

class User {
    public function __construct() {
        echo "This is the User class from MyApp namespace.";
    }
}
```

**File 2: `Product.php`**
```php
<?php
namespace MyApp;

class Product {
    public function __construct() {
        echo "This is the Product class from MyApp namespace.";
    }
}
```

**File 3: `index.php`**
```php
<?php
// Sử dụng từ khóa use để nhập lớp User từ namespace MyApp
use MyApp\User;
use MyApp\Product;

$user = new User();    // Output: This is the User class from MyApp namespace.
$product = new Product(); // Output: This is the Product class from MyApp namespace.
```

#### 3. Namespace lồng nhau:
Bạn có thể định nghĩa namespace lồng nhau giống như cấu trúc thư mục:
```php
<?php
namespace MyApp\Models;

class User {
    public function __construct() {
        echo "This is the User class from MyApp\Models namespace.";
    }
}
```

#### 4. Từ khóa `use`:
`use` giúp bạn dễ dàng sử dụng các lớp hoặc hàm từ namespace mà không cần gọi tên đầy đủ. Bạn cũng có thể đổi tên alias cho lớp hoặc hàm khi sử dụng:
```php
<?php
use MyApp\Models\User as MyUser;

$user = new MyUser();  // Sử dụng alias MyUser thay vì MyApp\Models\User
```

#### 5. Namespace toàn cục (global):
Nếu bạn muốn sử dụng một lớp hoặc hàm nằm ngoài namespace hiện tại, bạn có thể tham chiếu đến nó bằng cách sử dụng dấu `\` (backslash):
```php
<?php
namespace MyApp;

class User {
    public function __construct() {
        // Tham chiếu tới hàm count() trong global namespace
        echo \count([1, 2, 3]);  // Output: 3
    }
}
```

### Kết luận:
Namespace trong PHP là công cụ mạnh mẽ giúp bạn tổ chức mã tốt hơn, tránh xung đột tên, đặc biệt khi làm việc với các thư viện lớn hoặc dự án lớn.
