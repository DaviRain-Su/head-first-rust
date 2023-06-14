# 声明变量

在Rust中，变量是包含值的一块存储。可以使用变量声明为变量命名。只需使用let 关键字，后跟所需的名称以及变量将保存的值的类型。

```rust
let quantity: i32; //quantity 是变量名， i32是变量类型
let (length, width): (f64, f64); // 可以一次声明同一类型的多个变量
let customer_name: String;
```

一旦你声明了一个变量，就可以用=（这是一个单等号）为它分配该类型的任何值：

```rust
quantity = 2;
customer_name = "Damon Cole".to_string();
```

可以在同一语句中为多个变量赋值。只需将多个变量名放在=的左侧，将相同数量的值放在右侧，并使用逗号分隔。

```rust
(length, width) = (1.2, 2.4); // 一次为多个变量赋值
```
一旦给变量赋了值，你就可以在任何要使用原始值的上下文中使用它们：

```rust
fn main() {

    // 变量声明
    let quantity: i32; //quantity 是变量名， i32是变量类型
    let (length, width): (f64, f64); // 可以一次声明同一类型的多个变量
    let customer_name: String;

    // 给变量赋值
    quantity = 2;
    customer_name = "Damon Cole".to_string();
    (length, width) = (1.2, 2.4); // 一次为多个变量赋值

    // 使用变量
    println!("quantity: {quantity}");
    println!("length: {length}, width: {width}");
    println!("customer name: {customer_name}");
}
```

如果你事先知道变量的值是什么，你可以声明变量并在同一行赋值：

```rust
// 声明变量并赋值
let quantity: i32 = 4; // 只需要在末尾添加一个赋值
let (length, width): (f64, f64) = （1.2, 2.4); // 可以一次声明同一类型的多个变量
let customer_name: String = "Damon Cole".to_string();
```

你可以为现有变量分配新值，但它们必须是相同类型的值。Rust的静态类型确保你不会意外地将错误类型的值赋给变量。

```rust
quantity = "Damon Cole".to_string();
customer_name = 2;
```

```bash
error[E0308]: mismatched types
 --> src/main.rs:9:16
  |
5 |     let quantity: i32; //quantity 是变量名， i32是变量类型
  |                   --- expected due to this type
...
9 |     quantity = "Damon Cole".to_string();
  |                ^^^^^^^^^^^^^^^^^^^^^^^^ expected `i32`, found struct `String`

error[E0308]: mismatched types
  --> src/main.rs:10:21
   |
6  |     let customer_name: String;
   |                        ------ expected due to this type
...
10 |     customer_name = 2;
   |                     ^- help: try using a conversion method: `.to_string()`
   |                     |
   |                     expected struct `String`, found integer

For more information about this error, try `rustc --explain E0308`.
error: could not compile `playground` due to 2 previous errors
```
如果在声明变量的同时为其赋值，通常可以在声明中省略变量类型。这个分配给变量的值的类型将用作该变量的类型。

```rust
fn main() {

    // 变量声明并赋值
    let quantity = 2; //quantity 是变量名， i32是变量类型
    let (length, width) = (1.2, 2.4); // 可以一次声明同一类型的多个变量
    let customer_name = "Damon Cole".to_string();

    // 使用变量
    println!("quantity: {quantity}");
    println!("length: {length}, width: {width}");
    println!("customer name: {customer_name}");
}
```
