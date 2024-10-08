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
Trong PHP, câu lệnh `if...else` được sử dụng để thực hiện các quyết định điều kiện. Nó cho phép bạn thực thi các khối mã khác nhau dựa trên kết quả của một biểu thức điều kiện.

### 1. **Câu lệnh `if`**

Câu lệnh `if` kiểm tra một điều kiện. Nếu điều kiện đúng (trả về `true`), đoạn mã bên trong khối `if` sẽ được thực thi.

#### Cú pháp:
```php
if (điều_kiện) {
    // Khối lệnh sẽ được thực hiện nếu điều_kiện là true
}
```

#### Ví dụ:
```php
<?php
$age = 18;

if ($age >= 18) {
    echo "Bạn đủ tuổi để tham gia.";
}
?>
```

### Output:
```
Bạn đủ tuổi để tham gia.
```

Trong ví dụ này, điều kiện `$age >= 18` là đúng, vì vậy đoạn mã bên trong `if` được thực thi và in ra thông báo.

### 2. **Câu lệnh `if...else`**

Nếu điều kiện trong câu lệnh `if` không thỏa mãn (trả về `false`), khối lệnh bên trong `else` sẽ được thực thi.

#### Cú pháp:
```php
if (điều_kiện) {
    // Thực thi nếu điều_kiện là true
} else {
    // Thực thi nếu điều_kiện là false
}
```

#### Ví dụ:
```php
<?php
$age = 16;

if ($age >= 18) {
    echo "Bạn đủ tuổi để tham gia.";
} else {
    echo "Bạn chưa đủ tuổi để tham gia.";
}
?>
```

### Output:
```
Bạn chưa đủ tuổi để tham gia.
```

Ở đây, điều kiện `$age >= 18` là sai, vì vậy thông báo `"Bạn chưa đủ tuổi để tham gia."` sẽ được in ra.

### 3. **Câu lệnh `if...elseif...else`**

Khi bạn có nhiều điều kiện khác nhau, bạn có thể sử dụng thêm các câu lệnh `elseif` để kiểm tra nhiều điều kiện. Nếu một trong những điều kiện đúng, khối lệnh tương ứng sẽ được thực thi. Nếu không có điều kiện nào đúng, khối lệnh `else` sẽ được thực thi.

#### Cú pháp:
```php
if (điều_kiện_1) {
    // Thực thi nếu điều_kiện_1 là true
} elseif (điều_kiện_2) {
    // Thực thi nếu điều_kiện_1 là false và điều_kiện_2 là true
} else {
    // Thực thi nếu tất cả các điều kiện trên đều false
}
```

#### Ví dụ:
```php
<?php
$age = 15;

if ($age >= 18) {
    echo "Bạn đủ tuổi để tham gia.";
} elseif ($age >= 16) {
    echo "Bạn có thể tham gia với sự cho phép của người giám hộ.";
} else {
    echo "Bạn chưa đủ tuổi để tham gia.";
}
?>
```

### Output:
```
Bạn có thể tham gia với sự cho phép của người giám hộ.
```

Trong ví dụ này, vì điều kiện `$age >= 18` là sai nhưng `$age >= 16` là đúng, nên thông báo `"Bạn có thể tham gia với sự cho phép của người giám hộ."` sẽ được in ra.

### 4. **Câu lệnh `if` lồng nhau (nested if)**

Bạn có thể lồng câu lệnh `if...else` bên trong một câu lệnh `if...else` khác. Điều này giúp kiểm tra nhiều điều kiện phức tạp hơn.

#### Ví dụ:
```php
<?php
$age = 20;
$has_permission = true;

if ($age >= 18) {
    if ($has_permission) {
        echo "Bạn đủ tuổi và có quyền tham gia.";
    } else {
        echo "Bạn đủ tuổi nhưng không có quyền tham gia.";
    }
} else {
    echo "Bạn chưa đủ tuổi để tham gia.";
}
?>
```

### Output:
```
Bạn đủ tuổi và có quyền tham gia.
```

Ở đây, điều kiện đầu tiên kiểm tra nếu `$age >= 18` là đúng, sau đó kiểm tra thêm điều kiện `$has_permission` để quyết định thông báo sẽ hiển thị.

### 5. **Toán tử điều kiện (`ternary operator`)**

Toán tử điều kiện là một cách ngắn gọn để viết câu lệnh `if...else`. Nó có thể được sử dụng khi bạn cần kiểm tra một điều kiện đơn giản và thực thi một trong hai kết quả dựa trên điều kiện đó.

#### Cú pháp:
```php
biểu_thức ? giá_trị_nếu_true : giá_trị_nếu_false;
```

#### Ví dụ:
```php
<?php
$age = 20;
echo ($age >= 18) ? "Bạn đủ tuổi." : "Bạn chưa đủ tuổi.";
?>
```

### Output:
```
Bạn đủ tuổi.
```

Trong ví dụ này, toán tử điều kiện kiểm tra `$age >= 18`. Nếu đúng, sẽ in `"Bạn đủ tuổi."`, nếu sai, sẽ in `"Bạn chưa đủ tuổi."`.

### Tóm tắt:
- **`if...else`**: Được sử dụng để kiểm tra điều kiện và thực thi các khối mã khác nhau dựa trên giá trị đúng hoặc sai của điều kiện.
- **`elseif`**: Dùng để thêm điều kiện khi điều kiện `if` ban đầu không thỏa mãn.
- **Toán tử điều kiện**: Một cách viết tắt cho câu lệnh `if...else` đơn giản.
- **Câu lệnh `if` lồng nhau**: Kiểm tra các điều kiện phức tạp bằng cách lồng các câu lệnh `if` bên trong nhau.

## b. Vòng lặp
PHP hỗ trợ các vòng lặp như `for`, `while` và `foreach`.

### 1. **Vòng lặp `for`**

Vòng lặp `for` được sử dụng khi bạn biết trước số lần cần lặp. Nó gồm ba phần: khởi tạo, điều kiện lặp và cập nhật giá trị sau mỗi lần lặp.

#### Cú pháp:
```php
for (khởi_tạo; điều_kiện; cập_nhật) {
    // Khối lệnh sẽ được thực hiện
}
```

- **Khởi tạo**: Khởi tạo biến dùng để đếm số lần lặp, chỉ thực thi một lần lúc đầu.
- **Điều kiện**: Kiểm tra điều kiện trước mỗi lần lặp. Nếu điều kiện đúng thì tiếp tục lặp, nếu sai thì thoát vòng lặp.
- **Cập nhật**: Thực thi sau mỗi lần lặp để cập nhật biến đếm.

#### Ví dụ:
```php
<?php
for ($i = 1; $i <= 5; $i++) {
    echo "Số: $i <br>";
}
?>
```

### Output:
```
Số: 1
Số: 2
Số: 3
Số: 4
Số: 5
```

### 2. **Vòng lặp `while`**

Vòng lặp `while` thực hiện mã lệnh bên trong khi điều kiện vẫn còn đúng. Nó khác với `for` ở chỗ chỉ có điều kiện kiểm tra và không có phần khởi tạo hay cập nhật trong cú pháp.

#### Cú pháp:
```php
while (điều_kiện) {
    // Khối lệnh sẽ được thực hiện
}
```

- **Điều kiện**: Điều kiện này được kiểm tra trước mỗi lần lặp. Nếu đúng thì vòng lặp tiếp tục, nếu sai thì thoát vòng lặp.

#### Ví dụ:
```php
<?php
$i = 1;
while ($i <= 5) {
    echo "Số: $i <br>";
    $i++;
}
?>
```

### Output:
```
Số: 1
Số: 2
Số: 3
Số: 4
Số: 5
```

### 3. **Vòng lặp `do...while`**

Vòng lặp `do...while` tương tự như `while`, nhưng khác ở chỗ nó luôn thực hiện ít nhất một lần, bất kể điều kiện có đúng hay sai, vì điều kiện chỉ được kiểm tra sau khi đã thực thi khối lệnh.

#### Cú pháp:
```php
do {
    // Khối lệnh sẽ được thực hiện ít nhất một lần
} while (điều_kiện);
```

#### Ví dụ:
```php
<?php
$i = 1;
do {
    echo "Số: $i <br>";
    $i++;
} while ($i <= 5);
?>
```

### Output:
```
Số: 1
Số: 2
Số: 3
Số: 4
Số: 5
```

### 4. **Vòng lặp `foreach`**

Vòng lặp `foreach` được sử dụng đặc biệt cho các mảng hoặc đối tượng trong PHP. Nó duyệt qua từng phần tử của mảng mà không cần đến biến đếm.

#### Cú pháp:
```php
foreach ($mảng as $giá_trị) {
    // Khối lệnh sẽ được thực hiện cho mỗi phần tử
}

foreach ($mảng as $chỉ_số => $giá_trị) {
    // Khối lệnh với chỉ số và giá trị của từng phần tử
}
```

- **$giá_trị**: Là giá trị của mỗi phần tử trong mảng.
- **$chỉ_số**: Là chỉ số (key) của mỗi phần tử (nếu bạn muốn sử dụng).

#### Ví dụ duyệt qua giá trị:
```php
<?php
$fruits = ["Apple", "Banana", "Cherry"];

foreach ($fruits as $fruit) {
    echo "Trái cây: $fruit <br>";
}
?>
```

### Output:
```
Trái cây: Apple
Trái cây: Banana
Trái cây: Cherry
```

#### Ví dụ duyệt qua chỉ số và giá trị:
```php
<?php
$ages = ["Alice" => 25, "Bob" => 30, "Charlie" => 35];

foreach ($ages as $name => $age) {
    echo "$name is $age years old. <br>";
}
?>
```

### Output:
```
Alice is 25 years old.
Bob is 30 years old.
Charlie is 35 years old.
```

### 5. **Sự khác biệt chính giữa các loại vòng lặp**

| Vòng lặp    | Sử dụng khi                                                                                   | Đặc điểm chính                                                                 |
|-------------|------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| `for`       | Bạn biết trước số lần lặp.                                                                      | Có thể khởi tạo, kiểm tra điều kiện, và cập nhật biến lặp trong cùng một dòng. |
| `while`     | Bạn không biết trước số lần lặp, nhưng có điều kiện để kiểm tra trước mỗi lần lặp.               | Kiểm tra điều kiện trước khi lặp.                                              |
| `do...while`| Bạn muốn đảm bảo khối lệnh được thực thi ít nhất một lần, bất kể điều kiện ban đầu.              | Luôn thực thi ít nhất một lần.                                                 |
| `foreach`   | Bạn muốn duyệt qua tất cả các phần tử của mảng hoặc đối tượng.                                   | Chuyên dùng để duyệt mảng/đối tượng, không cần biến đếm.                       |

### Tóm tắt:
- **`for`**: Thích hợp cho các vòng lặp có số lần lặp cố định.
- **`while`**: Sử dụng khi cần kiểm tra điều kiện trước mỗi lần lặp và số lần lặp không xác định.
- **`do...while`**: Giống `while`, nhưng đảm bảo ít nhất một lần thực thi.
- **`foreach`**: Tối ưu khi làm việc với mảng hoặc đối tượng để duyệt qua tất cả phần tử.

## c. Switch 
Câu lệnh `switch` trong PHP là một cấu trúc điều kiện cho phép bạn so sánh một biến hoặc biểu thức với nhiều giá trị khác nhau (các trường hợp - `case`). Nó thường được sử dụng thay thế cho nhiều câu lệnh `if-else` lồng nhau khi bạn cần so sánh một giá trị với nhiều điều kiện.

### Cú pháp:
```php
switch (biểu_thức) {
    case giá_trị_1:
        // Thực thi nếu biểu_thức == giá_trị_1
        break;
    case giá_trị_2:
        // Thực thi nếu biểu_thức == giá_trị_2
        break;
    ...
    default:
        // Thực thi nếu không có case nào khớp
        break;
}
```

### Giải thích:
- **`switch (biểu_thức)`**: Biểu thức được kiểm tra trong câu lệnh `switch`. Nó có thể là một biến hoặc một giá trị cụ thể.
- **`case giá_trị_1:`**: Nếu giá trị của biểu thức bằng với `giá_trị_1`, đoạn mã bên dưới sẽ được thực thi.
- **`break;`**: Kết thúc việc thực thi trường hợp hiện tại và thoát khỏi câu lệnh `switch`. Nếu không có `break`, PHP sẽ tiếp tục kiểm tra các trường hợp tiếp theo, kể cả khi điều kiện trước đó đã thỏa mãn.
- **`default:`**: Tùy chọn này sẽ được thực thi nếu không có trường hợp `case` nào phù hợp với giá trị của biểu thức. Tương tự như `else` trong câu lệnh `if-else`.

### Ví dụ cơ bản:

```php
<?php
$day = "Monday";

switch ($day) {
    case "Monday":
        echo "Today is Monday.";
        break;
    case "Tuesday":
        echo "Today is Tuesday.";
        break;
    case "Wednesday":
        echo "Today is Wednesday.";
        break;
    default:
        echo "Unknown day.";
        break;
}
?>
```

### Output:
```
Today is Monday.
```

Trong ví dụ này, biến `$day` có giá trị `"Monday"`, do đó đoạn mã trong `case "Monday":` được thực thi và in ra chuỗi `"Today is Monday."`.

### Ví dụ nâng cao:

```php
<?php
$score = 85;

switch (true) {
    case ($score >= 90):
        echo "Grade: A";
        break;
    case ($score >= 80 && $score < 90):
        echo "Grade: B";
        break;
    case ($score >= 70 && $score < 80):
        echo "Grade: C";
        break;
    case ($score >= 60 && $score < 70):
        echo "Grade: D";
        break;
    default:
        echo "Grade: F";
        break;
}
?>
```

### Output:
```
Grade: B
```

Trong ví dụ này, `switch (true)` cho phép chúng ta so sánh các điều kiện phức tạp bằng cách sử dụng `case`. Giá trị của `$score` là `85`, vì vậy trường hợp `case ($score >= 80 && $score < 90)` thỏa mãn và in ra `"Grade: B"`.

### Sử dụng `switch` mà không có `break`:

Nếu bạn không sử dụng `break`, tất cả các trường hợp bên dưới trường hợp khớp sẽ được thực thi, ngay cả khi điều kiện đã được thỏa mãn. Điều này gọi là "fall-through".

#### Ví dụ:

```php
<?php
$day = "Monday";

switch ($day) {
    case "Monday":
        echo "It's Monday! ";
    case "Tuesday":
        echo "It's Tuesday! ";
    case "Wednesday":
        echo "It's Wednesday! ";
    default:
        echo "It's another day!";
}
?>
```

### Output:
```
It's Monday! It's Tuesday! It's Wednesday! It's another day!
```

Do không có `break`, tất cả các câu lệnh trong các `case` sau `"Monday"` cũng sẽ được thực thi.

### Kết luận:
- Câu lệnh `switch` giúp kiểm tra một giá trị với nhiều điều kiện khác nhau và thực thi mã khi một trường hợp khớp.
- `break` giúp ngăn việc thực thi các trường hợp sau khi một điều kiện đã được thỏa mãn.
- `default` được dùng để xử lý các trường hợp khi không có điều kiện nào khớp.
- `switch` có thể thay thế các câu lệnh `if-else` lồng nhau, giúp mã nguồn dễ đọc và bảo trì hơn.

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
- Get & Post method
```html
<form action="test.php" method="get">
  Name: <input type="text" name="name"><br>
  <input type="submit">
</form>

<?php
  echo $_GET["name"];
?>

```
```php
<?php
$username = $_POST['username'];
$password = $_POST['password'];
echo "Username: $username, Password: $password";
?>

```
- GET: Khi bạn cần lấy thông tin mà không làm thay đổi dữ liệu trên server, hoặc khi bạn muốn tạo liên kết mà người dùng có thể lưu lại hoặc chia sẻ.
- POST: Khi bạn cần gửi thông tin bảo mật, thông tin thay đổi dữ liệu (ví dụ: đăng ký, đăng nhập, thay đổi thông tin người dùng), hoặc khi lượng dữ liệu lớn hơn giới hạn của GET

# Checkbox in php
```html
<form action="test.php" method="post">
Apples: <input type="checkbox" name="fruits[]" value="apple"><br>
Bananas: <input type="checkbox" name="fruits[]" value="banana"><br>
<input type="submit">
</form>

<?php
$fruits = $_POST["fruits"];
echo $fruits[];
?>
```
# 6 Return statement
Trong PHP, câu lệnh `return` được sử dụng để kết thúc hàm và trả về một giá trị từ hàm đó. Khi PHP gặp lệnh `return`, quá trình thực thi của hàm dừng lại và giá trị sau `return` (nếu có) sẽ được trả về cho nơi gọi hàm.

### Cú pháp:
```php
return [giá trị];
```

- **[giá trị]**: Giá trị này có thể là bất cứ kiểu dữ liệu nào trong PHP, chẳng hạn như số nguyên, chuỗi, mảng, đối tượng, hoặc `null`. Nếu không có giá trị nào được cung cấp, mặc định PHP sẽ trả về `null`.

### 1. **Sử dụng `return` trong hàm**
`return` được dùng phổ biến nhất trong hàm để trả về kết quả:

#### Ví dụ:
```php
<?php
function add($a, $b) {
    return $a + $b;  // Trả về tổng của $a và $b
}

$result = add(5, 10);  // Hàm add trả về giá trị 15
echo $result;  // In ra 15
?>
```
- Ở đây, hàm `add` trả về kết quả của phép tính `$a + $b`, và giá trị đó được gán cho biến `$result`.

### 2. **Kết thúc hàm bằng `return`**
Câu lệnh `return` không chỉ dùng để trả về giá trị, mà còn có thể được dùng để kết thúc hàm sớm.

#### Ví dụ:
```php
<?php
function checkNumber($num) {
    if ($num <= 0) {
        return;  // Kết thúc hàm mà không trả về giá trị (mặc định là null)
    }
    echo "Số này lớn hơn 0: $num";
}

checkNumber(-5);  // Không in gì cả vì hàm đã kết thúc trước khi tới echo
checkNumber(10);  // In ra "Số này lớn hơn 0: 10"
?>
```
- Khi giá trị `$num` nhỏ hơn hoặc bằng 0, hàm sẽ dừng lại mà không thực thi tiếp các câu lệnh sau `return`.

### 3. **Trả về mảng hoặc đối tượng**
`return` cũng có thể được sử dụng để trả về mảng hoặc đối tượng.

#### Ví dụ trả về mảng:
```php
<?php
function getFruitList() {
    return ["Apple", "Banana", "Cherry"];  // Trả về mảng
}

$fruits = getFruitList();
print_r($fruits);
?>
```
- Hàm `getFruitList` trả về một mảng gồm 3 phần tử.

#### Ví dụ trả về đối tượng:
```php
<?php
class Person {
    public $name;
    public function __construct($name) {
        $this->name = $name;
    }
}

function createPerson($name) {
    return new Person($name);  // Trả về một đối tượng của lớp Person
}

$person = createPerson("Alice");
echo $person->name;  // In ra Alice
?>
```
- Hàm `createPerson` trả về một đối tượng của lớp `Person`.

### 4. **Trả về nhiều giá trị**
PHP không hỗ trợ trực tiếp việc trả về nhiều giá trị từ một hàm, nhưng bạn có thể trả về một mảng chứa nhiều giá trị.

#### Ví dụ:
```php
<?php
function getDimensions() {
    return [200, 100];  // Trả về một mảng chứa chiều dài và chiều rộng
}

list($length, $width) = getDimensions();  // Gán giá trị từ mảng trả về vào biến
echo "Chiều dài: $length, Chiều rộng: $width";  // In ra Chiều dài: 200, Chiều rộng: 100
?>
```

### 5. **Sự khác biệt giữa `return` và `echo`**
- **`return`**: Trả về giá trị từ hàm và kết thúc quá trình thực thi của hàm. Giá trị này có thể được sử dụng trong các biểu thức khác, gán cho biến, hoặc được xử lý tiếp.
- **`echo`**: In ra giá trị cho người dùng thấy (thường trên trình duyệt) nhưng không kết thúc hàm hoặc trả về giá trị để xử lý thêm.

#### So sánh:
```php
<?php
function returnExample() {
    return "This is returned.";
}

function echoExample() {
    echo "This is echoed.";
}

echo returnExample();  // In ra "This is returned."
echoExample();         // In ra "This is echoed."
?>
```

### Tổng kết:
- `return` được sử dụng để trả về một giá trị từ hàm và có thể kết thúc hàm sớm.
- Giá trị trả về có thể là bất kỳ kiểu dữ liệu nào và có thể được gán cho biến để sử dụng sau đó.
- `return` khác với `echo` ở chỗ nó không hiển thị kết quả trực tiếp mà chỉ trả về giá trị để xử lý tiếp trong chương trình.

# 7. Include statement 
Câu lệnh `include` trong PHP được sử dụng để chèn nội dung của một tệp PHP khác vào tệp hiện tại tại thời điểm chạy. Điều này rất hữu ích để tái sử dụng mã (code reuse), chẳng hạn như khi bạn có một phần nội dung cố định cần lặp lại trên nhiều trang, như phần đầu trang (header), chân trang (footer), hoặc các cấu hình chung.

### Cú pháp:
```php
include 'ten_tap_tin.php';
```

Trong đó, `ten_tap_tin.php` là đường dẫn đến tệp bạn muốn chèn. Đường dẫn có thể là tương đối hoặc tuyệt đối.

### Ví dụ cơ bản:
Giả sử bạn có tệp `header.php` chứa mã HTML cho phần đầu trang:

#### `header.php`:
```php
<!DOCTYPE html>
<html>
<head>
    <title>Trang của tôi</title>
</head>
<body>
<h1>Chào mừng bạn đến với trang của tôi</h1>
```

Bạn có thể sử dụng `include` để chèn nội dung của tệp này vào một tệp khác:

#### `index.php`:
```php
<?php include 'header.php'; ?>
<p>Đây là nội dung của trang chính.</p>
</body>
</html>
```

Khi chạy `index.php`, nội dung của `header.php` sẽ được chèn vào và hiển thị đầy đủ:

### Kết quả khi chạy `index.php`:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Trang của tôi</title>
</head>
<body>
<h1>Chào mừng bạn đến với trang của tôi</h1>
<p>Đây là nội dung của trang chính.</p>
</body>
</html>
```

### 1. **Công dụng của `include`:**
- **Tái sử dụng mã**: Bạn có thể lưu các phần mã dùng chung vào một tệp và chèn nó vào nhiều tệp khác bằng `include`.
- **Dễ bảo trì**: Nếu bạn cần thay đổi phần mã chung (như header hay footer), bạn chỉ cần sửa trong một tệp duy nhất, thay vì chỉnh sửa từng tệp một.
- **Cấu trúc mã rõ ràng hơn**: Giúp tách biệt các phần mã lớn và phức tạp thành các tệp riêng biệt.

### 2. **Sự khác biệt giữa `include` và `require`**:
- **`include`**: Nếu tệp được chèn không tồn tại hoặc có lỗi, PHP sẽ phát ra một cảnh báo (`warning`) nhưng vẫn tiếp tục chạy mã.
- **`require`**: Nếu tệp không tồn tại hoặc có lỗi, PHP sẽ phát ra lỗi nghiêm trọng (`fatal error`) và dừng thực thi.

#### Ví dụ về `include`:
```php
<?php
include 'khong_ton_tai.php';  // Tệp này không tồn tại
echo "Trang vẫn tiếp tục chạy!";
?>
```

### Output:
```
Warning: include(khong_ton_tai.php): failed to open stream: No such file or directory in index.php on line 2
Trang vẫn tiếp tục chạy!
```

Trong trường hợp này, PHP cảnh báo lỗi nhưng vẫn tiếp tục thực thi câu lệnh `echo`.

#### Ví dụ về `require`:
```php
<?php
require 'khong_ton_tai.php';  // Tệp này không tồn tại
echo "Trang vẫn tiếp tục chạy!";
?>
```

### Output:
```
Fatal error: require(): Failed opening required 'khong_ton_tai.php' in index.php on line 2
```

Với `require`, chương trình sẽ dừng lại và không thực thi các dòng lệnh sau đó.

### 3. **Sử dụng `include_once` và `require_once`:**
- **`include_once`**: Đảm bảo rằng tệp được chèn chỉ một lần duy nhất, ngay cả khi nó được gọi nhiều lần.
- **`require_once`**: Tương tự `include_once`, nhưng có hành vi giống `require`, nghĩa là nếu tệp không tồn tại, sẽ gây ra lỗi nghiêm trọng và dừng chương trình.

#### Ví dụ về `include_once`:
```php
<?php
include_once 'header.php';
include_once 'header.php';  // Lần thứ hai sẽ bị bỏ qua
?>
```

Trong ví dụ này, tệp `header.php` chỉ được chèn một lần, dù bạn gọi `include_once` nhiều lần.

### Tóm tắt:
- **`include`**: Chèn nội dung của tệp khác vào mã hiện tại. Nếu tệp không tồn tại, chương trình vẫn tiếp tục chạy nhưng sẽ phát ra cảnh báo.
- **`require`**: Tương tự `include`, nhưng nếu tệp không tồn tại, chương trình sẽ dừng chạy ngay lập tức.
- **`include_once`** và **`require_once`**: Đảm bảo tệp chỉ được chèn một lần duy nhất trong suốt quá trình chạy chương trình, tránh tình trạng chèn lặp lại không cần thiết.
-------

# 8. Kết nối với MySQL
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
