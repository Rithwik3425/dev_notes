# Set 1

1. Design the following static web pages required for an online book store web site. 
		 a. HOMEPAGE: 
		 b. LOGINPAGE 
		 c. CATALOGEPAGE
* Home Page
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Online Bookstore</title>
    <!-- Add your CSS link here -->
    <style>
        /* Add your CSS styles here */
        .book {
            border: 1px solid #ccc;
            padding: 10px;
            margin-bottom: 20px;
            display: inline-block;
            width: 200px;
        }
        .book img {
            width: 100%;
            height: auto;
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header>
        <h1>Welcome to Our Online Bookstore</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="catalog.html">Catalog</a></li>
                <li><a href="login.html">Login</a></li>
            </ul>
        </nav>
        <form action="#" method="get">
            <input type="text" placeholder="Search books...">
            <button type="submit">Search</button>
        </form>
    </header>

    <!-- Featured Books Section -->
    <section id="featured-books">
        <h2>Featured Books</h2>
        <div class="book">
            <img src="book1.jpg" alt="Book 1">
            <h3>Book Title 1</h3>
            <p>Author: Author Name</p>
            <p>Price: $10.99</p>
        </div>
        <div class="book">
            <img src="book2.jpg" alt="Book 2">
            <h3>Book Title 2</h3>
            <p>Author: Author Name</p>
            <p>Price: $12.99</p>
        </div>
        <div class="book">
            <img src="book3.jpg" alt="Book 3">
            <h3>Book Title 3</h3>
            <p>Author: Author Name</p>
            <p>Price: $9.99</p>
        </div>
    </section>

    <!-- Categories Section -->
    <section id="categories">
        <h2>Categories</h2>
        <ul>
            <li><a href="#">Fiction</a></li>
            <li><a href="#">Non-Fiction</a></li>
            <li><a href="#">Science Fiction</a></li>
            <li><a href="#">Mystery</a></li>
            <li><a href="#">Thriller</a></li>
            <li><a href="#">Romance</a></li>
        </ul>
    </section>

    <!-- Footer Section -->
    <footer>
        <p>Contact us: info@bookstore.com</p>
        <ul>
            <li><a href="#">Facebook</a></li>
            <li><a href="#">Twitter</a></li>
            <li><a href="#">Instagram</a></li>
        </ul>
        <p>&copy; 2024 Online Bookstore. All rights reserved.</p>
    </footer>
</body>
</html>

```
* Login page
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <!-- Add your CSS link here -->
</head>
<body>
    <h1>Login</h1>
    <form action="login.php" method="post">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br><br>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br><br>
        <input type="submit" value="Login">
    </form>
    <p>Don't have an account? <a href="register.html">Register here</a></p>
    <!-- Forgot password link (optional) -->
</body>
</html>
```
* Catalouge page
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catalog</title>
    <!-- Add your CSS link here -->
</head>
<body>
    <h1>Book Catalog</h1>
    <!-- Filter options -->
    <!-- List of books -->
    <!-- Pagination -->
</body>
</html>
```
2. JSP program calculates Powers of 2 for integers in the range 0-10
```jsp
<%@ page language="java" %>
<%@ page import="java.io.*, java.util.*" %>

<!DOCTYPE html>
<html>
<head>
    <title>Powers of 2</title>
</head>
<body>
    <h2>Powers of 2 for Integers in the Range 0-10</h2>
    <%
        for (int i = 0; i <= 10; i++) {
            out.println("2^" + i + " = " + Math.pow(2, i) + "<br>");
        }
    %>
</body>
</html>
```
3. Write a PHP code to check whether given string is palindrome or not
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Palindrome Checker</title>
</head>
<body>
    <h2>Palindrome Checker</h2>
    <form method="post">
        <label for="string">Enter a string:</label>
        <input type="text" id="string" name="string" required>
        <input type="submit" value="Check">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $string = $_POST["string"];
        if (strtolower($string) == strrev(strtolower($string))) {
            echo "<p>'$string' is a palindrome.</p>";
        } else {
            echo "<p>'$string' is not a palindrome.</p>";
        }
    }
    ?>
</body>
</html>
```
---

# Set 2

1. Design the scientific calculator and make event for each button using JavaScript.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scientific Calculator</title>
    <style>
        /* Add your CSS styles here */
        button {
            width: 50px;
            height: 50px;
            margin: 5px;
        }
    </style>
</head>
<body>
    <div>
        <input type="text" id="display" readonly>
    </div>
    <div>
        <button onclick="clearDisplay()">C</button>
        <button onclick="addToDisplay('**')">^</button>
        <button onclick="addToDisplay('%')">%</button>
        <button onclick="addToDisplay('/')">/</button>
    </div>
    <div>
        <button onclick="addToDisplay('7')">7</button>
        <button onclick="addToDisplay('8')">8</button>
        <button onclick="addToDisplay('9')">9</button>
        <button onclick="addToDisplay('*')">*</button>
    </div>
    <div>
        <button onclick="addToDisplay('4')">4</button>
        <button onclick="addToDisplay('5')">5</button>
        <button onclick="addToDisplay('6')">6</button>
        <button onclick="addToDisplay('-')">-</button>
    </div>
    <div>
        <button onclick="addToDisplay('1')">1</button>
        <button onclick="addToDisplay('2')">2</button>
        <button onclick="addToDisplay('3')">3</button>
        <button onclick="addToDisplay('+')">+</button>
    </div>
    <div>
        <button onclick="addToDisplay('0')">0</button>
        <button onclick="calculate()">=</button>
    </div>
    <script>
        // JavaScript code for calculator functionality
        function addToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculate() {
            try {
                document.getElementById('display').value = eval(document.getElementById('display').value);
            } catch (error) {
                document.getElementById('display').value = 'Error';
            }
        }
    </script>
</body>
</html>
```
2. Write a jsp program for registration page (username, password, email, mobileno, clgname).
```html
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration</title>
</head>
<body>
    <h2>Registration Form</h2>
    <form action="registration_process.jsp" method="post">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br><br>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br><br>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>
        <label for="mobileno">Mobile No:</label>
        <input type="text" id="mobileno" name="mobileno" required><br><br>
        <label for="clgname">College Name:</label>
        <input type="text" id="clgname" name="clgname" required><br><br>
        <input type="submit" value="Register">
    </form>
</body>
</html>

```
3. PHP program to swap two numbers
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Swapper</title>
</head>
<body>
    <h2>Number Swapper</h2>
    <form method="post">
        <label for="num1">Enter first number:</label>
        <input type="number" id="num1" name="num1" required><br><br>
        <label for="num2">Enter second number:</label>
        <input type="number" id="num2" name="num2" required><br><br>
        <input type="submit" value="Swap">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $num1 = $_POST["num1"];
        $num2 = $_POST["num2"];

        echo "<p>Before swapping:</p>";
        echo "<p>First number: $num1</p>";
        echo "<p>Second number: $num2</p>";

        // Swapping logic
        $temp = $num1;
        $num1 = $num2;
        $num2 = $temp;

        echo "<p>After swapping:</p>";
        echo "<p>First number: $num1</p>";
        echo "<p>Second number: $num2</p>";
    }
    ?>
</body>
</html>
```
---

# Set 3

1. Design the following static web pages with the following attributes: 
a. Basic Tags.  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Tags</title>
</head>
<body>
    <h1>This is a Heading</h1>
    <p>This is a paragraph.</p>
    <a href="#">This is a link</a>
    <br>
    <img src="image.jpg" alt="Image">
</body>
</html>
```
b. Heading Tags.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Heading Tags</title>
</head>
<body>
    <h1>Heading 1</h1>
    <h2>Heading 2</h2>
    <h3>Heading 3</h3>
    <h4>Heading 4</h4>
    <h5>Heading 5</h5>
    <h6>Heading 6</h6>
</body>
</html>

```
c. List (Ordered and Un-Ordered).
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>List Tags</title>
</head>
<body>
    <h2>Ordered List</h2>
    <ol>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
    </ol>

    <h2>Unordered List</h2>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
    </ul>
</body>
</html>

```


2. Write a jsp program to display the details of registered page.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registered Page Details</title>
</head>
<body>
    <h2>User Details</h2>
    <%
        String username = "John Doe";
        String email = "john@example.com";
        String mobileNo = "1234567890";
        String collegeName = "ABC College";
    %>
    <p>Username: <%= username %></p>
    <p>Email: <%= email %></p>
    <p>Mobile No: <%= mobileNo %></p>
    <p>College Name: <%= collegeName %></p>
</body>
</html>

```
3. Assume a variable “a “initialize its value to 1229. Using PHP code check whether the no. is prime or not
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Number Checker</title>
</head>
<body>
    <h2>Prime Number Checker</h2>
    <?php
        $a = 1229;
        $isPrime = true;
        
        if ($a <= 1) {
            $isPrime = false;
        } else {
            for ($i = 2; $i <= sqrt($a); $i++) {
                if ($a % $i == 0) {
                    $isPrime = false;
                    break;
                }
            }
        }
        
        if ($isPrime) {
            echo "<p>$a is a prime number.</p>";
        } else {
            echo "<p>$a is not a prime number.</p>";
        }
    ?>
</body>
</html>
```
---

# Set 4

1. Design a static web pages with the following attributes: 
a. BUTTON
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Button</title>
</head>
<body>
    <h2>Button</h2>
    <button type="button">Click Me</button>
</body>
</html>

```
b. RADIO BUTTON
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Radio Button</title>
</head>
<body>
    <h2>Radio Button</h2>
    <input type="radio" id="option1" name="option" value="option1">
    <label for="option1">Option 1</label><br>
    <input type="radio" id="option2" name="option" value="option2">
    <label for="option2">Option 2</label><br>
    <input type="radio" id="option3" name="option" value="option3">
    <label for="option3">Option 3</label><br>
</body>
</html>

```
c. DROP DOWN
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drop Down</title>
</head>
<body>
    <h2>Drop Down</h2>
    <label for="cars">Choose a car:</label>
    <select id="cars" name="cars">
        <option value="volvo">Volvo</option>
        <option value="saab">Saab</option>
        <option value="mercedes">Mercedes</option>
        <option value="audi">Audi</option>
    </select>
</body>
</html>

```
2. Write a jsp program to demonstrate param action tag. 
```html
<!-- param_action.jsp -->
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Param Action Tag</title>
</head>
<body>
    <h2>Param Action Tag Example</h2>
    <c:param name="firstName" value="John" />
    <c:param name="lastName" value="Doe" />
    <c:redirect url="welcome.jsp" />
</body>
</html>

```
3. PHP program to print factorial of a number.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Factorial Calculator</title>
</head>
<body>
    <h2>Factorial Calculator</h2>
    <?php
        function factorial($n) {
            if ($n <= 1) {
                return 1;
            } else {
                return $n * factorial($n - 1);
            }
        }

        $number = 5; // Change this to the desired number
        echo "Factorial of $number is " . factorial($number);
    ?>
</body>
</html>
```
---

# Set 5

1. Embedding JavaScript in HTML pages.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Embedding</title>
    <script>
        function greet() {
            alert('Hello, World!');
        }
    </script>
</head>
<body>
    <h2>Embedding JavaScript in HTML</h2>
    <button onclick="greet()">Click Me</button>
</body>
</html>

```
2. Write a jsp program to find Fibonacci series.
```html
<!-- fibonacci.jsp -->
<%@ page import="java.io.*" %>
<%@ page import="java.util.*" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fibonacci Series</title>
</head>
<body>
    <h2>Fibonacci Series</h2>
    <% 
        int n = 10; // Change this to the desired number of terms
        int a = 0, b = 1;
        out.print(a + ", " + b + ", ");
        for (int i = 2; i < n; i++) {
            int next = a + b;
            out.print(next + ", ");
            a = b;
            b = next;
        }
    %>
</body>
</html>
```
3. PHP code to Reverse String with and Without using strrev() function.
with using strrev() function
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reverse String with strrev()</title>
</head>
<body>
    <h2>Reverse String with strrev() Function</h2>
    <?php
        $string = "Hello, World!";
        echo "Original String: $string<br>";
        $reversedString = strrev($string);
        echo "Reversed String: $reversedString";
    ?>
</body>
</html>

```

without using strrev() function
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reverse String without strrev()</title>
</head>
<body>
    <h2>Reverse String without strrev() Function</h2>
    <?php
        $string = "Hello, World!";
        echo "Original String: $string<br>";
        $length = strlen($string);
        $reversedString = '';
        for ($i = $length - 1; $i >= 0; $i--) {
            $reversedString .= $string[$i];
        }
        echo "Reversed String: $reversedString";
    ?>
</body>
</html>
```
---

# set 6

1. Program to create a class calculator that contains an   overloaded method called "add" to calculate the sum of two integers, two float numbers and, one integer and one float.
```javascript
class Calculator {
    // Method to add two integers
    add(a, b) {
        return a + b;
    }

    // Method to add two floats
    addFloat(a, b) {
        return a + b;
    }

    // Method to add one integer and one float
    addMixed(a, b) {
        return a + b;
    }
}

// Testing the calculator class
const calc = new Calculator();
console.log("Sum of integers: " + calc.add(5, 7));
console.log("Sum of floats: " + calc.addFloat(3.5, 2.5));
console.log("Sum of mixed types: " + calc.addMixed(10, 2.5));
```
2. Write a jsp program to check whether given no is palindrome or not.
```html
<!-- palindrome.jsp -->
<%@ page language="java" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Palindrome Checker</title>
</head>
<body>
    <h2>Palindrome Checker</h2>
    <%!
        boolean isPalindrome(int num) {
            int originalNum = num;
            int reversedNum = 0;
            while (num != 0) {
                int digit = num % 10;
                reversedNum = reversedNum * 10 + digit;
                num /= 10;
            }
            return originalNum == reversedNum;
        }
    %>
    <% 
        int number = 12321; // Change this to the desired number
        if (isPalindrome(number)) {
            out.println("<p>" + number + " is a palindrome.</p>");
        } else {
            out.println("<p>" + number + " is not a palindrome.</p>");
        }
    %>
</body>
</html>
```
3. Write a PHP code to add n number of numbers by creating add() function.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Add Numbers</title>
</head>
<body>
    <h2>Add Numbers</h2>
    <?php
        function add() {
            $args = func_get_args();
            $sum = 0;
            foreach ($args as $num) {
                $sum += $num;
            }
            return $sum;
        }

        $result = add(5, 10, 15, 20); // Change the numbers as needed
        echo "<p>The sum is: $result</p>";
    ?>
</body>
</html>
```
---

# Set 7

1. Design the following static web pages required for an online book store web site.   
A) HOMEPAGE
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Online Bookstore</title>
    <style>
        /* Add your CSS styles here */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }
        nav ul {
            list-style-type: none;
            padding: 0;
        }
        nav ul li {
            display: inline;
            margin-right: 20px;
        }
        section {
            padding: 20px;
        }
        footer {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
            position: absolute;
            bottom: 0;
            width: 100%;
        }
        footer ul {
            list-style-type: none;
            padding: 0;
            margin-top: 10px;
        }
        footer ul li {
            display: inline;
            margin-right: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to Our Online Bookstore</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="catalog.html">Catalog</a></li>
                <li><a href="login.html">Login</a></li>
            </ul>
        </nav>
    </header>

    <section id="featured-books">
        <h2>Featured Books</h2>
        <div class="book">
            <img src="book1.jpg" alt="Book 1">
            <h3>Book Title 1</h3>
            <p>Author: Author Name</p>
            <p>Price: $10.99</p>
        </div>
        <div class="book">
            <img src="book2.jpg" alt="Book 2">
            <h3>Book Title 2</h3>
            <p>Author: Author Name</p>
            <p>Price: $12.99</p>
        </div>
        <div class="book">
            <img src="book3.jpg" alt="Book 3">
            <h3>Book Title 3</h3>
            <p>Author: Author Name</p>
            <p>Price: $9.99</p>
        </div>
    </section>

    <section id="categories">
        <h2>Categories</h2>
        <ul>
            <li><a href="#">Fiction</a></li>
            <li><a href="#">Non-Fiction</a></li>
            <li><a href="#">Science Fiction</a></li>
            <li><a href="#">Mystery</a></li>
            <li><a href="#">Thriller</a></li>
            <li><a href="#">Romance</a></li>
        </ul>
    </section>

    <section id="about">
        <h2>About Us</h2>
        <p>Welcome to our online bookstore! We offer a wide range of books in various genres. Whether you're into fiction, non-fiction, mystery, or romance, we have something for everyone. Browse our catalog to find your next favorite read!</p>
    </section>

    <footer>
        <p>Contact us: info@bookstore.com</p>
        <ul>
            <li><a href="#">Facebook</a></li>
            <li><a href="#">Twitter</a></li>
            <li><a href="#">Instagram</a></li>
        </ul>
        <p>&copy; 2024 Online Bookstore. All rights reserved.</p>
    </footer>
</body>
</html>
```
B) LOGINPAGE
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
</head>
<body>
    <h1>Login</h1>
    <form action="login.php" method="post">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br><br>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br><br>
        <input type="submit" value="Login">
    </form>
    <p>Don't have an account? <a href="register.html">Register here</a></p>
</body>
</html>
```
2. Write a jsp program to find factorial of a number.
```html
<%@ page language="java" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Factorial Calculator</title>
</head>
<body>
    <h2>Factorial Calculator</h2>
    <% 
        int number = 5; // Change this to the desired number
        int factorial = 1;
        for (int i = 1; i <= number; i++) {
            factorial *= i;
        }
    %>
    <p>Factorial of <%= number %> is <%= factorial %></p>
</body>
</html>
```
3. PHP code to check whether no. is even or odd
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Even Odd Checker</title>
</head>
<body>
    <h2>Even Odd Checker</h2>
    <?php
        $number = 10; // Change this to the desired number
        if ($number % 2 == 0) {
            echo "<p>$number is even.</p>";
        } else {
            echo "<p>$number is odd.</p>";
        }
    ?>
</body>
</html>
```
---

# set 8

1. Write a Program to create popup boxes in Java Script.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Popup Boxes in JavaScript</title>
</head>
<body>
    <h2>Popup Boxes in JavaScript</h2>
    <button onclick="alert('This is an alert box!')">Show Alert</button>
    <button onclick="confirm('Are you sure?')">Show Confirm</button>
    <button onclick="prompt('Please enter your name:', 'John')">Show Prompt</button>
</body>
</html>
```
2. Write a JSP code to demonstrate declaration tag and scriplet tag.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JSP Declaration and Scriptlet Tags</title>
</head>
<body>
    <h2>JSP Declaration and Scriptlet Tags</h2>
    <%!
        String message = "Hello, World!";
    %>
    <p><%= message %></p>
    <% 
        for (int i = 0; i < 5; i++) {
    %>
            <p><%= "This is line " + (i+1) %></p>
    <%
        }
    %>
</body>
</html>
```
3. Write a PHP code to print the following pattern. 
```
* * * * * 
* * * *
* * * 
* *
* 
```

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Print Pattern in PHP</title>
</head>
<body>
    <h2>Pattern in PHP</h2>
    <?php
        for ($i = 5; $i >= 1; $i--) {
            for ($j = 1; $j <= $i; $j++) {
                echo "* ";
            }
            echo "<br>";
        }
    ?>
</body>
</html>
```
---

# Set 9

1. Demonstrate selectors(group,universal,child,descendent).
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Selectors Demo</title>
    <style>
        /* Group Selector */
        h1, p {
            color: blue;
        }

        /* Universal Selector */
        * {
            margin: 0;
            padding: 0;
        }

        /* Child Selector */
        div > p {
            font-weight: bold;
        }

        /* Descendant Selector */
        div p {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1>Group Selector</h1>
    <p>This is a paragraph.</p>
    <div>
        <p>This is a bold paragraph.</p>
        <span>This is not a paragraph.</span>
    </div>
</body>
</html>
```
2. Write a JSP code to demonstrate exceptional handling.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JSP Exception Handling</title>
</head>
<body>
    <h2>JSP Exception Handling</h2>
    <% 
        try {
            int result = 10 / 0; // Division by zero will throw ArithmeticException
            out.println("Result: " + result);
        } catch (ArithmeticException e) {
            out.println("An arithmetic error occurred: " + e.getMessage());
        }
    %>
</body>
</html>

```
3. PHP code to demonstrate $x (single dollar) and $ $x (double dollar).
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP Variable Demonstration</title>
</head>
<body>
    <h2>PHP Variable Demonstration</h2>
    <?php
        // $x
        $x = "Hello";
        echo "$x<br>"; // Prints Hello

        // $$x
        $y = "x";
        echo "${$y}<br>"; // Prints the value of $x, i.e., Hello
    ?>
</body>
</html>
```
---

# Set 10

1. Write a java script program to find whether number is palindrome or not
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Palindrome Checker</title>
</head>
<body>
    <h2>Palindrome Checker</h2>
    <script>
        function isPalindrome(number) {
            const numString = number.toString();
            const reversedNumString = numString.split('').reverse().join('');
            return numString === reversedNumString;
        }

        const num = 12321; // Change this to the desired number
        if (isPalindrome(num)) {
            document.write(num + " is a palindrome.");
        } else {
            document.write(num + " is not a palindrome.");
        }
    </script>
</body>
</html>
```
2. Write a JSP program for session tracking using 
a.	Hidden fields
```html
<!-- session_hidden.jsp -->
<%@ page language="java" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Session Tracking using Hidden Fields</title>
</head>
<body>
    <h2>Session Tracking using Hidden Fields</h2>
    <form action="session_hidden.jsp" method="post">
        <input type="hidden" name="sessionId" value="<%= session.getId() %>">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br><br>
        <input type="submit" value="Submit">
    </form>
</body>
</html>
```
b. Url Rewriting
```html
<!-- session_url.jsp -->
<%@ page language="java" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Session Tracking using URL Rewriting</title>
</head>
<body>
    <h2>Session Tracking using URL Rewriting</h2>
    <a href="session_url.jsp?sessionId=<%= session.getId() %>">Visit Here</a>
</body>
</html>
```
c. Cookies
```html
<!-- session_cookies.jsp -->
<%@ page language="java" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Session Tracking using Cookies</title>
</head>
<body>
    <h2>Session Tracking using Cookies</h2>
    <% 
        Cookie sessionIdCookie = new Cookie("sessionId", session.getId());
        sessionIdCookie.setMaxAge(3600); // Cookie will expire in 1 hour
        response.addCookie(sessionIdCookie);
    %>
    <p>Session ID stored in cookie.</p>
</body>
</html>
```
d. Session objects
```html
<!-- session_objects.jsp -->
<%@ page language="java" %>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Session Tracking using Session Objects</title>
</head>
<body>
    <h2>Session Tracking using Session Objects</h2>
    <%
        String sessionId = session.getId();
        session.setAttribute("sessionId", sessionId);
    %>
    <p>Session ID stored in session object.</p>
</body>
</html>
```
3. PHP program to check leap year.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Leap Year Checker</title>
</head>
<body>
    <h2>Leap Year Checker</h2>
    <?php
        function isLeapYear($year) {
            if (($year % 4 == 0 && $year % 100 != 0) || $year % 400 == 0) {
                return true;
            } else {
                return false;
            }
        }

        $year = 2024; // Change this to the desired year
        if (isLeapYear($year)) {
            echo "<p>$year is a leap year.</p>";
        } else {
            echo "<p>$year is not a leap year.</p>";
        }
    ?>
</body>
</html>
```
---

# Set 11

1. Write JavaScript code that uses recursion.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Recursion in JavaScript</title>
    <script>
        function factorial(n) {
            if (n === 0 || n === 1) {
                return 1;
            } else {
                return n * factorial(n - 1);
            }
        }

        // Example usage
        console.log("Factorial of 5: " + factorial(5));
    </script>
</head>
<body>
    <h2>Recursion in JavaScript</h2>
    <!-- You can also call the function from here if needed -->
</body>
</html>
```
2. Write a jsp program to demonstrate forward action tag.
```html
<!-- forward_demo.jsp -->
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Forward Action Tag Demo</title>
</head>
<body>
    <h2>Forward Action Tag Demo</h2>
    <p>This is the forward_demo.jsp page.</p>
    <%-- Forwarding to another JSP page --%>
    <%@ page import="java.io.*" %>
    <%@ page import="javax.servlet.*" %>
    <%@ page import="javax.servlet.http.*" %>
    <% 
        // Forwarding using request dispatcher
        RequestDispatcher rd = request.getRequestDispatcher("target_page.jsp");
        rd.forward(request, response);
    %>
</body>
</html>
```
3. PHP program to check for an Armstrong number.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Armstrong Number Checker</title>
</head>
<body>
    <h2>Armstrong Number Checker</h2>
    <?php
        function isArmstrong($number) {
            $sum = 0;
            $temp = $number;
            $numDigits = strlen((string)$number);
            while ($temp != 0) {
                $digit = $temp % 10;
                $sum += $digit ** $numDigits;
                $temp = intval($temp / 10);
            }
            return $sum === $number;
        }
        $num = 153; // Change this to the desired number
        if (isArmstrong($num)) {
            echo "<p>$num is an Armstrong number.</p>";
        } else {
            echo "<p>$num is not an Armstrong number.</p>";
        }
    ?>
</body>
</html>
```
---

# Set 12

1. Create  table to display marks of a student using html tags.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Marks Table</title>
</head>
<body>
    <h2>Student Marks</h2>
    <table border="1">
        <tr>
            <th>Subject</th>
            <th>Marks</th>
        </tr>
        <tr>
            <td>Math</td>
            <td>90</td>
        </tr>
        <tr>
            <td>Science</td>
            <td>85</td>
        </tr>
        <tr>
            <td>English</td>
            <td>88</td>
        </tr>
    </table>
</body>
</html>
```
2. Write a jsp program to find Fibonacci series.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fibonacci Series</title>
</head>
<body>
    <h2>Fibonacci Series</h2>
    <% 
        int n = 10; // Change this to the desired number of terms
        int a = 0, b = 1;
        out.print(a + ", " + b + ", ");
        for (int i = 2; i < n; i++) {
            int next = a + b;
            out.print(next + ", ");
            a = b;
            b = next;
        }
    %>
</body>
</html>
```
3. PHP program to reverse a number
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reverse Number</title>
</head>
<body>
    <h2>Reverse Number</h2>
    <?php
        function reverseNumber($num) {
            $reversedNum = 0;
            while ($num != 0) {
                $digit = $num % 10;
                $reversedNum = $reversedNum * 10 + $digit;
                $num = intval($num / 10);
            }
            return $reversedNum;
        }

        $number = 12345; // Change this to the desired number
        $reversed = reverseNumber($number);
        echo "<p>Original Number: $number</p>";
        echo "<p>Reversed Number: $reversed</p>";
    ?>
</body>
</html>
```
---

# set 13

1. Demonstrat pseudo classes (first child, lastchild, onlychild, nth child).
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pseudo-classes Demo</title>
    <style>
        /* First Child */
        ul li:first-child {
            color: red;
        }

        /* Last Child */
        ul li:last-child {
            color: blue;
        }

        /* Only Child */
        ul li:only-child {
            font-weight: bold;
        }

        /* Nth Child */
        ul li:nth-child(2n) {
            background-color: lightgray;
        }
    </style>
</head>
<body>
    <h2>Pseudo-classes Demo</h2>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
        <li>Item 4</li>
        <li>Item 5</li>
    </ul>
</body>
</html>
```
2. Write a JSP program to find reverses of the given number?
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reverse Number</title>
</head>
<body>
    <h2>Reverse Number</h2>
    <%
        int number = 12345; // Change this to the desired number
        int reversed = 0;
        while (number != 0) {
            int digit = number % 10;
            reversed = reversed * 10 + digit;
            number /= 10;
        }
        out.println("Reverse of the given number: " + reversed);
    %>
</body>
</html>
```
3. PHP code to print the Fibonaaci Series taking an input from HTML form
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fibonacci Series</title>
</head>
<body>
    <h2>Fibonacci Series</h2>
    <form action="fibonacci.php" method="post">
        <label for="terms">Enter number of terms:</label>
        <input type="text" id="terms" name="terms" required>
        <input type="submit" value="Generate Series">
    </form>
</body>
</html>
```
```php
<!-- fibonacci.php -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fibonacci Series</title>
</head>
<body>
    <h2>Fibonacci Series</h2>
    <?php
        function fibonacci($n) {
            $first = 0;
            $second = 1;
            $series = "$first, $second";
            for ($i = 2; $i < $n; $i++) {
                $next = $first + $second;
                $series .= ", $next";
                $first = $second;
                $second = $next;
            }
            return $series;
        }

        if ($_SERVER["REQUEST_METHOD"] == "POST") {
            $terms = $_POST["terms"];
            echo "<p>Fibonacci Series for $terms terms:</p>";
            echo "<p>" . fibonacci($terms) . "</p>";
        }
    ?>
</body>
</html>
```
---

# Set 14

1. Write a HTML code to display this webpage.
```html

```
2. Find the time difference between the last created cookie and current cookie?
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Time Difference Between Cookies</title>
</head>
<body>
    <h2>Time Difference Between Cookies</h2>
    <%
        // Get the value of the lastCreatedCookie
        Cookie[] cookies = request.getCookies();
        String lastCreatedCookieValue = null;
        for (Cookie cookie : cookies) {
            if (cookie.getName().equals("lastCreatedCookie")) {
                lastCreatedCookieValue = cookie.getValue();
                break;
            }
        }

        // Get the current time
        long currentTime = System.currentTimeMillis();

        // Calculate the time difference
        long lastCookieTime = Long.parseLong(lastCreatedCookieValue);
        long timeDifference = currentTime - lastCookieTime;

        // Convert milliseconds to hours, minutes, and seconds
        long secondsDifference = timeDifference / 1000;
        long minutesDifference = secondsDifference / 60;
        long hoursDifference = minutesDifference / 60;

        out.println("Time difference between the last created cookie and the current cookie: " + hoursDifference + " hours, " + (minutesDifference % 60) + " minutes, " + (secondsDifference % 60) + " seconds.");
    %>
</body>
</html>
```
3. Write a PHP program to count the number of vowels in a given string.
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Count Vowels in PHP</title>
</head>
<body>
    <h2>Count Vowels in PHP</h2>
    <?php
        function countVowels($str) {
            $vowels = ['a', 'e', 'i', 'o', 'u'];
            $count = 0;
            for ($i = 0; $i < strlen($str); $i++) {
                if (in_array(strtolower($str[$i]), $vowels)) {
                    $count++;
                }
            }
            return $count;
        }

        $inputString = "Hello World"; // Change this to the desired string
        $numVowels = countVowels($inputString);
        echo "<p>Number of vowels in '$inputString': $numVowels</p>";
    ?>
</body>
</html>
```
---

# Set 15

1. Write a java script program to check if  number is perfect or not.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perfect Number Checker</title>
</head>
<body>
    <h2>Perfect Number Checker</h2>
    <script>
        function isPerfectNumber(num) {
            let sum = 1;
            for (let i = 2; i <= Math.sqrt(num); i++) {
                if (num % i === 0) {
                    sum += i;
                    if (i !== num / i) {
                        sum += num / i;
                    }
                }
            }
            return sum === num && num !== 1;
        }

        const number = 28; // Change this to the desired number
        if (isPerfectNumber(number)) {
            document.write(number + " is a perfect number.");
        } else {
            document.write(number + " is not a perfect number.");
        }
    </script>
</body>
</html>
```
2. Write a jsp program to demonstrate scriptlets.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JSP Scriptlets Demo</title>
</head>
<body>
    <h2>JSP Scriptlets Demo</h2>
    <% 
        String name = "John";
        out.println("Welcome, " + name + "!");
    %>
</body>
</html>
```
3. Write PHP code that takes a student's marks as input and prints out the corresponding grade based on the following grading system:
A+: 90 or above
A: 80-89
B+: 70-79
B: 60-69
C+: 50-59
C: 40-49
D: 30-39
F: Below 30
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Calculator</title>
</head>
<body>
    <h2>Grade Calculator</h2>
    <?php
        $marks = 85; // Change this to the student's marks
        echo "<p>Student's Marks: $marks</p>";
        if ($marks >= 90) {
            echo "<p>Grade: A+</p>";
        } elseif ($marks >= 80) {
            echo "<p>Grade: A</p>";
        } elseif ($marks >= 70) {
            echo "<p>Grade: B+</p>";
        } elseif ($marks >= 60) {
            echo "<p>Grade: B</p>";
        } elseif ($marks >= 50) {
            echo "<p>Grade: C+</p>";
        } elseif ($marks >= 40) {
            echo "<p>Grade: C</p>";
        } elseif ($marks >= 30) {
            echo "<p>Grade: D</p>";
        } else {
            echo "<p>Grade: F</p>";
        }
    ?>
</body>
</html>
```
---
