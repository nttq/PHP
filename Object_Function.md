Trong PHP, **object function** (hàm đối tượng) hay còn gọi là **phương thức (methods)** là các hàm được định nghĩa bên trong một lớp và có thể được gọi thông qua đối tượng của lớp đó. Các phương thức này hoạt động như các hành động mà đối tượng có thể thực hiện, và chúng có thể truy cập các thuộc tính của đối tượng thông qua từ khóa `this`.

### 1. **Tạo object function trong lớp (class)**

Khi bạn định nghĩa một lớp trong PHP, bạn có thể định nghĩa các phương thức bên trong nó. Các phương thức này có 
thể tương tác với các thuộc tính của đối tượng để thực hiện các nhiệm vụ khác nhau.

#### Ví dụ cơ bản:

```php
<?php
// Định nghĩa lớp Person
class Person {
    public $name;   // Thuộc tính name
    public $age;    // Thuộc tính age

    // Hàm thiết lập giá trị cho thuộc tính name
    public function setName($name) {
        $this->name = $name;
    }

    // Hàm thiết lập giá trị cho thuộc tính age
    public function setAge($age) {
        $this->age = $age;
    }

    // Hàm trả về thông tin người
    public function getInfo() {
        return $this->name . " is " . $this->age . " years old.";
    }
}

// Tạo đối tượng từ lớp Person
$person1 = new Person();

// Gọi các phương thức để thiết lập và lấy thông tin
$person1->setName("John");
$person1->setAge(25);

echo $person1->getInfo(); // Output: John is 25 years old.
?>
```

#### Giải thích:
- **Phương thức `setName()` và `setAge()`**: Đây là các hàm dùng để gán giá trị cho các thuộc tính `$name` và `$age` của đối tượng.
- **Phương thức `getInfo()`**: Trả về một chuỗi chứa thông tin của đối tượng.
- **`$this`**: Từ khóa này đại diện cho đối tượng hiện tại và được dùng để truy cập các thuộc tính và phương thức bên trong lớp.

### 2. **Cách gọi hàm đối tượng**

Hàm đối tượng (phương thức) được gọi thông qua đối tượng đã được tạo từ lớp bằng cách sử dụng toán tử `->`.

#### Cú pháp:
```php
$object->methodName();
```

Ví dụ:
```php
$person1->setName("John"); // Gọi phương thức setName()
```

### 3. **Phạm vi truy cập của phương thức**

Phương thức trong PHP có thể có các phạm vi truy cập sau:
- **`public`**: Phương thức có thể được truy cập từ bất kỳ đâu.
- **`protected`**: Phương thức chỉ có thể được truy cập từ bên trong lớp hoặc các lớp kế thừa.
- **`private`**: Phương thức chỉ có thể được truy cập từ bên trong chính lớp đó, không thể truy cập từ bên ngoài.

#### Ví dụ:

```php
<?php
class MyClass {
    public function publicMethod() {
        echo "This is a public method.";
    }

    protected function protectedMethod() {
        echo "This is a protected method.";
    }

    private function privateMethod() {
        echo "This is a private method.";
    }

    public function accessMethods() {
        $this->publicMethod();
        $this->protectedMethod();
        $this->privateMethod();
    }
}

$myObject = new MyClass();
$myObject->publicMethod();  // Truy cập được
// $myObject->protectedMethod(); // Lỗi! Không thể truy cập phương thức protected
// $myObject->privateMethod();   // Lỗi! Không thể truy cập phương thức private
$myObject->accessMethods();  // Truy cập tất cả các phương thức thông qua phương thức public
?>
```

### 4. **Hàm khởi tạo (Constructor) và hàm hủy (Destructor)**

- **Constructor (`__construct`)**: Là phương thức đặc biệt được gọi tự động khi một đối tượng được tạo ra từ lớp. Nó thường được sử dụng để khởi tạo các thuộc tính của đối tượng.
- **Destructor (`__destruct`)**: Là phương thức đặc biệt được gọi tự động khi một đối tượng bị hủy (kết thúc chương trình hoặc đối tượng không còn được sử dụng).

#### Ví dụ về hàm khởi tạo và hàm hủy:

```php
<?php
class Car {
    public $brand;
    public $color;

    // Constructor được gọi khi đối tượng được tạo ra
    public function __construct($brand, $color) {
        $this->brand = $brand;
        $this->color = $color;
        echo "Tạo xe $brand có màu $color.<br>";
    }

    // Destructor được gọi khi đối tượng bị hủy
    public function __destruct() {
        echo "Đối tượng xe $this->brand đã bị hủy.";
    }

    public function displayInfo() {
        echo "Xe $this->brand có màu $this->color.<br>";
    }
}

$myCar = new Car("Toyota", "Đỏ");  // Constructor tự động được gọi
$myCar->displayInfo();  // Gọi phương thức để hiển thị thông tin
// Khi kết thúc chương trình, hàm __destruct sẽ tự động được gọi
?>
```

### Output:
```
Tạo xe Toyota có màu Đỏ.
Xe Toyota có màu Đỏ.
Đối tượng xe Toyota đã bị hủy.
```

### 5. **Phương thức tĩnh (Static method)**

Phương thức tĩnh là phương thức có thể được gọi mà không cần tạo đối tượng của lớp. Bạn sử dụng từ khóa `static` để khai báo phương thức tĩnh. Để gọi phương thức tĩnh, bạn sử dụng toán tử `::` thay vì `->`.

#### Ví dụ về phương thức tĩnh:

```php
<?php
class Math {
    // Phương thức tĩnh
    public static function add($a, $b) {
        return $a + $b;
    }
}

// Gọi phương thức tĩnh mà không cần tạo đối tượng
echo Math::add(5, 10);  // Output: 15
?>
```

### 6. **Tóm tắt**
- **Phương thức (Methods)** là các hàm được định nghĩa bên trong lớp và có thể thực hiện hành động nào đó trên đối tượng.
- **Gọi phương thức**: Sử dụng toán tử `->` để gọi phương thức của đối tượng. Đối với phương thức tĩnh, sử dụng `::`.
- **Phạm vi truy cập**: Các phương thức có thể là `public`, `protected`, hoặc `private`.
- **Hàm khởi tạo (`__construct`) và hàm hủy (`__destruct`)**: Là các phương thức đặc biệt được gọi tự động khi đối tượng được tạo và khi đối tượng bị hủy.
- **Phương thức tĩnh**: Được gọi trực tiếp từ lớp mà không cần tạo đối tượng.
