# 零值（未初始化变量）


如果声明一个变量而没有给它赋值，该变量就是一个没有初始化的变量。如果需要表示一个类型为空可以使用Option类型：

```rust
let quantity: u32;
println!("quantity: {quantity}");

error[E0381]: used binding `quantity` isn't initialized
 --> src/main.rs:5:26
  |
4 |     let quantity: u32;
  |         -------- binding declared here but left uninitialized
5 |     println!("quantity: {quantity}");
  |                          ^^^^^^^^ `quantity` used here but it isn't initialized
  |
  = note: this error originates in the macro `$crate::format_args_nl` which comes from the expansion of the macro `println` (in Nightly builds, run with -Z macro-backtrace for more info)
help: consider assigning a value
  |
4 |     let quantity: u32 = 0;
  |                       +++

For more information about this error, try `rustc --explain E0381`.
error: could not compile `playground` due to previous error
```

可以使用Option包装u32类型。

```rust
let quantity: Option<u32> = None;
println!("quantity: {quantity:?}"); //output quantity: None
```
