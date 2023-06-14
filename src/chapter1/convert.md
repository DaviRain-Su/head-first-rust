# 转换

Rust中的数学运算和比较运算要求包含的值具有相同的类型。如果不是的话，则在尝试运行代码时会报错。

```rust
let length: f64 = 1.2; //设置一个float64变量
let width: u32 = 2; // 设置一个int变量
println!("Area is {}", length * width); // 如果我们在数学运算中同时使用float64浮点数和整数类型.....
println!("length > width ? {}", length > width); // 或者比较 ...
```

```bash
error: argument never used
 --> src/main.rs:6:34
  |
6 |     println!("length > width ?", length > width); // 或者比较 ...
  |              ------------------  ^^^^^^^^^^^^^^ argument never used
  |              |
  |              formatting specifier missing

error[E0277]: cannot multiply `f64` by `u32`
 --> src/main.rs:5:35
  |
5 |     println!("Area is {}", length * width); // 如果我们在数学运算中同时使用float64浮点数和整数类型.....
  |                                   ^ no implementation for `f64 * u32`
  |
  = help: the trait `Mul<u32>` is not implemented for `f64`
  = help: the following other types implement trait `Mul<Rhs>`:
            <&'a f64 as Mul<f64>>
            <&f64 as Mul<&f64>>
            <f64 as Mul<&f64>>
            <f64 as Mul>

error[E0308]: mismatched types
 --> src/main.rs:6:43
  |
6 |     println!("length > width ?", length > width); // 或者比较 ...
  |                                           ^^^^^ expected `f64`, found `u32`
  |
help: you can convert a `u32` to an `f64`, producing the floating point representation of the integer
  |
6 |     println!("length > width ?", length > width.into()); // 或者比较 ...
  |                                                +++++++

Some errors have detailed explanations: E0277, E0308.
For more information about an error, try `rustc --explain E0277`.
error: could not compile `playground` due to 3 previous errors
```

为变量分配新值也是如此。如果所赋值的类型与变量的声明类型不匹配，也会报错。

```rust
let mut length: f64 = 1.2; //设置一个float64变量
let width: u32 = 2; // 设置一个int变量
length = width; // 如果我们将int值赋值给f64变量
println!("{length}");
```

```bash
error[E0308]: mismatched types
 --> src/main.rs:5:10
  |
3 |     let mut length: f64 = 1.2;
  |                     --- expected due to this type
4 | let width: u32 = 2;
5 | length = width;
  |          ^^^^^ expected `f64`, found `u32`
  |
help: you can convert a `u32` to an `f64`, producing the floating point representation of the integer
  |
5 | length = width.into();
  |               +++++++


For more information about this error, try `rustc --explain E0308`.
error: could not compile `playground` due to previous error
```

解决方法是使用转换，它允许你将值从一种类型转换为另一种类型。只需提供要将值转换成的类型，as 后面跟上要转换的类型，这种用法仅仅对于Rust语言的一些原生类型，对于复杂类型还需要实现From,Into trait。

```rust
let my_int: i32 = 2;
let my_float = my_int as f64;
```

上面这段代码运行不会报错，可见这种转换方式是正确的。

让我们更新失败的代码示例，在任何数学运算中，或者与其他f64值进行比较前，先将u32值转换为f64值。

```rust
let length: f64 = 1.2; //设置一个float64变量
let width: u32 = 2; // 设置一个int变量
println!("Area is {}", length * width as f64); // 如果我们在数学运算中同时使用float64浮点数和整数类型.....
println!("length > width ? {}", length > width as f64); // 或者比较 ...

// output:
// Area is 2.4
// length > width ? false
```

数学运算和比较现在都能正常工作！现在让我们尝试在将一个u32值转换为f64之前，先把它赋值给f64变量：

```rust
let mut length: f64 = 1.2; //设置一个float64变量
let width: u32 = 2; // 设置一个int变量
length = width as f64; // 如果我们将int值赋值给f64变量
println!("{length}"); // output: 2
```

同样，转换就绪后，赋值成功了。在进行转换时，请注意它们可能会如何更改结果值。例如，f64变量可以存储小数值，但是u32变量不能。当你将f64转换为u32时，小数部分会被简单地删掉！这可能会抛弃用结果值执行的任何操作

```rust
let length: f64 = 3.75; //设置一个float64变量
let mut width: u32 = 5; // 设置一个int变量
width  = length as u32; // 如果我们将int值赋值给f64变量
println!("{width}"); // output: 3
```

不过只要你保持谨慎，你就会发现转换在使用Rust时是必不可少的。它们允许不兼容的类型一起工作。
