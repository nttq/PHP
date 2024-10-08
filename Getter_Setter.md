Trong PHP, **getter** và **setter** là các phương thức đặc biệt trong lập trình hướng đối tượng (OOP) được sử dụng để truy cập và cập nhật các thuộc tính (properties) của một đối tượng. Chúng thường được sử dụng khi bạn muốn kiểm soát cách dữ liệu được gán vào hoặc lấy ra từ một đối tượng, thay vì truy cập trực tiếp vào các thuộc tính.

### 1. **Getter (Hàm lấy dữ liệu)**

Getter là một phương thức được sử dụng để lấy giá trị của một thuộc tính từ một đối tượng. Nó thường bắt đầu với tiền tố `get`.

#### Cú pháp getter:
```php
public function getPropertyName() {
    return $this->propertyName;
}
```

### 2. **Setter (Hàm gán dữ liệu)**

Setter là một phương thức được sử dụng để gán giá trị cho một thuộc tính của đối tượng. Nó thường bắt đầu với tiền tố `set`. Setter cũng cho phép bạn kiểm tra hoặc sửa đổi dữ liệu trước khi gán cho thuộc tính.

#### Cú pháp setter:
```php
public function setPropertyName($value) {
    $this->propertyName = $value;
}
```

### 3. **Ví dụ về getter và setter trong PHP**

Dưới đây là ví dụ về một lớp `Person` có các thuộc tính như `name` và `age`, với các getter và setter tương ứng:

```php
<?php
class Person {
    // Thuộc tính private, chỉ truy cập được qua getter và setter
    private $name;
    private $age;

    // Getter cho thuộc tính name
    public function getName() {
        return $this->name;
    }

    // Setter cho thuộc tính name
    public function setName($name) {
        $this->name = $name;
    }

    // Getter cho thuộc tính age
    public function getAge() {
        return $this->age;
    }

    // Setter cho thuộc tính age
    public function setAge($age) {
        // Kiểm tra nếu age hợp lệ (lớn hơn 0)
        if ($age > 0) {
            $this->age = $age;
        } else {
            echo "Tuổi không hợp lệ!";
        }
    }
}

// Tạo đối tượng Person
$person = new Person();

// Sử dụng setter để gán giá trị cho thuộc tính
$person->setName("John");
$person->setAge(25);

// Sử dụng getter để lấy giá trị của thuộc tính
echo $person->getName();  // Output: John
echo $person->getAge();   // Output: 25
?>
```

### 4. **Tại sao sử dụng getter và setter?**

- **Kiểm soát truy cập**: Getter và setter giúp bạn kiểm soát chặt chẽ hơn cách mà các thuộc tính của đối tượng được truy cập hoặc sửa đổi.
- **Bảo mật dữ liệu**: Thay vì cho phép người dùng hoặc mã khác trực tiếp truy cập và sửa đổi thuộc tính, bạn có thể sử dụng setter để kiểm tra tính hợp lệ của giá trị trước khi gán.
- **Ẩn chi tiết triển khai**: Người sử dụng lớp không cần biết chi tiết về cách dữ liệu được lưu trữ hoặc tính toán, họ chỉ cần gọi các getter và setter.

### 5. **Phạm vi truy cập và getter/setter**

Thông thường, các thuộc tính của lớp được khai báo với phạm vi **private** để ngăn chặn truy cập trực tiếp từ bên ngoài lớp. Để truy cập những thuộc tính này, bạn cần sử dụng getter và setter với phạm vi **public**.

Ví dụ:
```php
class BankAccount {
    private $balance;

    // Getter cho balance
    public function getBalance() {
        return $this->balance;
    }

    // Setter cho balance
    public function setBalance($balance) {
        if ($balance >= 0) {
            $this->balance = $balance;
        } else {
            echo "Số dư không hợp lệ!";
        }
    }
}

$account = new BankAccount();
$account->setBalance(100);  // Đặt số dư thành 100
echo $account->getBalance(); // Lấy số dư
```

### 6. **Tóm tắt**

- **Getter**: Phương thức lấy giá trị của thuộc tính. Thường bắt đầu với từ "get".
- **Setter**: Phương thức gán giá trị cho thuộc tính. Thường bắt đầu với từ "set" và có thể bao gồm logic kiểm tra giá trị.
- Getter và setter giúp bảo vệ thuộc tính, đảm bảo tính hợp lệ của dữ liệu và cung cấp cách kiểm soát tốt hơn đối với các thuộc tính của đối tượng.

Getter và setter là một phần quan trọng trong việc kiểm soát và bảo vệ dữ liệu trong lập trình hướng đối tượng.
