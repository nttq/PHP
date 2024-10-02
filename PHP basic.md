# 1. Bắt đầu với PHP
## a. Thiết lập môi trường
- Máy chủ web: Apache hoặc Nginx (một phần của các gói XAMPP hoặc MAMP)
- PHP: Trình thông dịch cho ngôn ngữ PHP.
- MySQL (tùy chọn cho công việc cơ sở dữ liệu): Thường được sử dụng với PHP cho các trang web động.

## b. Cú pháp PHP cơ bản
Các tập lệnh PHP được thực thi trên máy chủ và kết quả được trả về trình duyệt dưới dạng HTML thuần túy. Có thể chèn PHP vào mã HTML của bằng thẻ `<?php ... ?>`.

```html
<!DOCTYPE html>
<html>
<body>

<h1>Trang PHP đầu tiên của tôi</h1>

<?php
echo "Hello, World!";
?>

</body>
</html>
```

- `<?php ... ?>`: Mã PHP nằm bên trong các thẻ này.
- `echo`: Xuất nội dung ra trang web.
- Lưu tệp này với phần mở rộng `.php`, ví dụ: `index.php`.

## c. Biến
Biến PHP bắt đầu bằng dấu $
- String: Văn bản (`"Xin chào"`)
- Integer: Số nguyên (`123`)
- float: Số thập phân (`3.14`)
- Boolean: Đúng hoặc sai (`true` hoặc `false`)
- array: Một tập hợp các giá trị ( `[1, 2, 3] `)
- Object: Một thể hiện của một lớp.

## e. Các toán tử cơ bản
- Số học: `+`, `-`, `*`, `/`, `%` (modulo)
- Bài tập: `=`, `+=`, `-=`, `*=`, `/=`
- So sánh: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Logic: `&&` (AND), `||` (OR), `!` (NOT)

## f. var_dump function
-> see what a variable contains 
ex: 
```php 
<?php
$message = "Hello, Tu Quyen!"
$age = 22
$height = 1.52

var_dump($message);
?>
```
=> Output: string(16)"Hello, Tu Quyen!"

##h. Nối chuỗi trong php (dùng dấu . )
```php 
<?php
$message = "Hello";
$name = "Quyen"

echo $message . " " . $name
?>
```
=> Output: Hello Tu Quyen

# 2. Cấu trúc điều khiển

## a. If-Else
Kiểm soát luồng chương trình bằng các câu lệnh điều kiện.

```php
<?php
$age = 20;
if ($age >= 18) {
echo "Bạn là người lớn.";
} else {
echo "Bạn chưa phải là người lớn.";
}
?>
```

## b. Vòng lặp
PHP hỗ trợ các vòng lặp như `for`, `while` và `foreach`.

- Vòng lặp For:

```php
<?php
for ($i = 0; $i < 5; $i++) {
echo "Số: $i<br>";
}
?>
```

- Vòng lặp While:

```php
<?php
$i = 0;
while ($i < 5) {
echo "Số: $i<br>";
$i++;
}
?>
```

- Vòng lặp Foreach (dùng cho mảng):

```php
<?php
$colors = ["red", "green", "blue"];
foreach ($colors as $color) {
echo "Màu: $color<br>";
}
?>
```

## c. Switch 
```php
<?php

$day= "Tue";

Switch($day){
  Case "Mon":
      echo "Monday";
       break;
  Case "Tue":
      echo "Tuesday";
       break;
  Case ...
       break;
  Default:
      echo "unavailble";
      break;
}

?>
```

# 3. Hàm
Bạn có thể tạo các khối mã có thể tái sử dụng trong PHP bằng các hàm.

```php
<?php
function greet($name) {
return "Hello, $name!";
}
echo greet("Alice");
?>
```

- Hàm có thể có tham số và trả về giá trị.
- Bạn có thể sử dụng `return` để gửi giá trị trở lại cho người gọi.
# Array in PHP
- Array có thể chứa nhiều kiểu dữ liệu
- 1 Array có thể chứa nhiều arrays nhỏ bên trong, các arrays con ngăn cách nhau bởi dấu `,`
- Only integers and strings can be used as array indexes
  ## Syntax
  ```php
  $data = [];
  $data = array();
  ```

```php
<?php
$information = [
  "message" => "Hello ",
  "name" => "Tu Quyen",
  "age" => 22,
  "height" => 1.52,
  "status" => false
  "relationship" => null
  ];
?>
```
- Mảng PHP cho phép bạn lưu trữ nhiều giá trị trong một biến duy nhất.

```php
<?php
$numbers = [1, 2, 3, 4, 5];
echo $numbers[0]; // Đầu ra 1
?>
```

- Mảng kết hợp: Mảng có khóa là chuỗi thay vì số.

```php
<?php
$ages = ["Alice" => 25, "Bob" => 30];
echo $ages["Alice"]; // Đầu ra 25
?>
```
> Create a variable called array that contains an array with three simple values. These values can be whatever you like. Explicitly assign the string index of "third" to the third element. Write a foreach  loop that contains the following statement to print out each element of the array, along with its index: echo "$index = $value.";


# 5. Làm việc với Biểu mẫu
PHP có thể được sử dụng để xử lý dữ liệu biểu mẫu HTML.

- Biểu mẫu HTML:

```html
<form method="POST" action="process.php">
Tên: <input type="text" name="name">
<input type="submit" value="Submit">
</form>
```

- PHP để xử lý việc gửi biểu mẫu (process.php):

```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
$name = $_POST['name'];
echo "Xin chào, $name!";

}
?>
```

# 6. Kết nối với MySQL
PHP có thể tương tác với cơ sở dữ liệu MySQL bằng PDO hoặc MySQLi.

```php
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "test_db";

// Tạo kết nối
$conn = new mysqli($servername, $username, $password, $dbname);

// Kiểm tra kết nối
if ($conn->connect_error) {
die("Kết nối không thành công: " . $conn->connect_error);
}

$sql = "SELECT id, name FROM users";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
while($row = $result->fetch_assoc()) {
echo "id: " . $row["id"]. " - Name: " . $row["name"]. "<br>";
}
} else {
echo "0 results";
}
$conn->close();
?>
```
