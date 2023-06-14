# println!宏

## println!宏 在 Rust 中

println! 是 Rust 中一个非常常用的宏，用于打印输出信息到标准输出流。下面将介绍该宏的基本使用方法和一些常见的格式化选项。

## 基本使用方法

println! 宏的语法结构为：

```rust
println!(format_string, argument1, argument2, ...)
```

其中 format_string 用于指定输出格式，argument1, argument2, ... 则是要输出的变量值。下面是一个简单的例子：

```rust
let name = "Alice";
let age = 25;
println!("My name is {} and I'm {} years old.", name, age);
```

输出结果为：

```bash
My name is Alice and I'm 25 years old.
```

常见的格式化选项

println! 宏支持多种格式化选项，下面列举一些常见的用法：

- {}：用于输出变量的值，自动匹配变量类型。
- {:<width>}：用于指定输出宽度，左对齐。
- {:>width}：用于指定输出宽度，右对齐。
- {:^width}：用于指定输出宽度，居中对齐。
- {:.precision}：用于指定输出精度，适用于浮点数类型。

下面是一些具体的例子：

```rust
let pi = 3.14159265358979323846;
println!("Pi is approximately {:.2}", pi);
```

输出结果为：

```bash
Pi is approximately 3.14
```

```rust
let name = "Bob";
let age = 35;
println!("{0:<10} is {1:>5} years old.", name, age);
```

输出结果为：

```bash
Bob        is    35 years old.
```

## 总结

本文介绍了 println! 宏在 Rust 中的基本使用方法和常见的格式化选项。
