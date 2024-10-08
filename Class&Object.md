Trong PHP, **class (lớp)** và **object (đối tượng)** là nền tảng của lập trình hướng đối tượng (OOP). Chúng giúp bạn tổ chức mã và tạo ra các thực thể có thể tái sử dụng với các thuộc tính và hành vi.

### 1. **Class (Lớp)**

Một **lớp** trong PHP là một khuôn mẫu hoặc bản thiết kế cho các đối tượng. Nó định nghĩa các thuộc tính (biến) và phương thức (hàm) mà đối tượng của nó sẽ có.

#### Cú pháp tạo lớp:

```php
<?php
class ClassName {
    // Thuộc tính (properties)
    public $property1;
    public $property2;

    // Phương thức (methods)
    public function method1() {
        // Nội dung của phương thức
    }
}
?>
```

- **`$property1`, `$property2`**: Đây là các thuộc tính của lớp, có thể lưu trữ dữ liệu cho đối tượng.
- **`method1`**: Đây là phương thức, định nghĩa các hành động mà đối tượng có thể thực hiện.

### 2. **Object (Đối tượng)**

Một **đối tượng** là một thực thể cụ thể được tạo từ một lớp. Khi bạn tạo ra một đối tượng, nó sẽ kế thừa các thuộc tính và phương thức từ lớp mà nó được tạo ra.

#### Cú pháp tạo đối tượng từ lớp:

```php
$object = new ClassName();
```

#### Ví dụ:

```php
<?php
// Định nghĩa lớp Car
class Car {
    public $brand;  // Thuộc tính thương hiệu xe
    public $color;  // Thuộc tính màu xe

    // Phương thức thiết lập thương hiệu
    public function setBrand($brand) {
        $this->brand = $brand;
    }

    // Phương thức thiết lập màu sắc
    public function setColor($color) {
        $this->color = $color;
    }

    // Phương thức để hiển thị thông tin xe
    public function displayInfo() {
        echo "Xe thương hiệu " . $this->brand . " có màu " . $this->color . ".";
    }
}

// Tạo đối tượng từ lớp Car
$myCar = new Car();
$myCar->setBrand("Toyota");  // Đặt thương hiệu là Toyota
$myCar->setColor("Đỏ");      // Đặt màu sắc là đỏ
$myCar->displayInfo();        // Gọi phương thức hiển thị thông tin xe
?>
```

### Output:
```
Xe thương hiệu Toyota có màu Đỏ.
```

#### Giải thích:
- **`$myCar`** là một đối tượng của lớp `Car`.
- **`$this->brand`** và **`$this->color`** được sử dụng để truy cập các thuộc tính của đối tượng hiện tại trong phương thức của lớp.
- **`new Car()`** tạo ra một đối tượng mới từ lớp `Car`.
- Phương thức `setBrand()` và `setColor()` được gọi để thiết lập giá trị cho các thuộc tính của đối tượng.

### 3. **Thuộc tính và Phương thức**
- **Thuộc tính (Properties)**: Là biến được khai báo bên trong một lớp và chứa dữ liệu liên quan đến đối tượng.
- **Phương thức (Methods)**: Là các hàm bên trong lớp, xác định hành động mà đối tượng có thể thực hiện.

#### Ví dụ về thuộc tính và phương thức:
```php
class Person {
    public $name;
    public $age;

    public function setName($name) {
        $this->name = $name;
    }

    public function setAge($age) {
        $this->age = $age;
    }

    public function getInfo() {
        return $this->name . " is " . $this->age . " years old.";
    }
}

$person = new Person();
$person->setName("John");
$person->setAge(30);
echo $person->getInfo();  // Output: John is 30 years old.
```

### 4. **Phạm vi truy cập (Access Modifiers)**

Trong PHP, có ba loại phạm vi truy cập:
- **`public`**: Có thể truy cập từ bất kỳ đâu (trong và ngoài lớp).
- **`protected`**: Chỉ có thể truy cập từ bên trong lớp hoặc các lớp con.
- **`private`**: Chỉ có thể truy cập từ bên trong lớp.

#### Ví dụ:
```php
class User {
    public $username;  // Có thể truy cập ở bất kỳ đâu
    protected $email;  // Chỉ truy cập từ trong lớp và các lớp con
    private $password; // Chỉ truy cập từ trong lớp

    public function setPassword($password) {
        $this->password = $password;
    }
}
```

### 5. **Constructor (Hàm khởi tạo)**

Hàm khởi tạo là một phương thức đặc biệt được gọi tự động khi một đối tượng được tạo ra. Trong PHP, hàm khởi tạo được định nghĩa bằng tên `__construct()`.

#### Ví dụ:
```php
class Animal {
    public $name;
    public $type;

    // Hàm khởi tạo
    public function __construct($name, $type) {
        $this->name = $name;
        $this->type = $type;
    }

    public function getInfo() {
        return "Con vật " . $this->name . " thuộc loại " . $this->type . ".";
    }
}

$dog = new Animal("Chó", "Thú cưng");
echo $dog->getInfo();  // Output: Con vật Chó thuộc loại Thú cưng.
```

Trong ví dụ này, hàm `__construct()` tự động được gọi khi đối tượng `$dog` được tạo, và nó gán giá trị cho thuộc tính `$name` và `$type`.

### 6. **Kế thừa (Inheritance)**

Một lớp có thể kế thừa từ một lớp khác để chia sẻ các thuộc tính và phương thức. Lớp con sẽ kế thừa mọi thứ từ lớp cha, nhưng có thể mở rộng thêm hoặc ghi đè phương thức.

#### Ví dụ:
```php
class Vehicle {
    public $brand;

    public function setBrand($brand) {
        $this->brand = $brand;
    }

    public function getBrand() {
        return $this->brand;
    }
}

class Car extends Vehicle {
    public function drive() {
        echo "Xe " . $this->getBrand() . " đang chạy!";
    }
}

$car = new Car();
$car->setBrand("Honda");
$car->drive();  // Output: Xe Honda đang chạy!
```

### 7. **Tóm tắt**:
- **Class (Lớp)**: Là khuôn mẫu để tạo đối tượng, chứa các thuộc tính và phương thức.
- **Object (Đối tượng)**: Là một thực thể cụ thể của lớp, có thể truy cập và sử dụng các thuộc tính và phương thức của lớp.
- **Constructor (Hàm khởi tạo)**: Được gọi tự động khi đối tượng được tạo, dùng để khởi tạo giá trị ban đầu cho đối tượng.
- **Kế thừa**: Một lớp có thể kế thừa từ lớp khác để tái sử dụng mã và mở rộng chức năng.
