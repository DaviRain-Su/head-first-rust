# 函数返回值

在 Rust 中，函数的返回值由 -> 符号后的类型指定。一个函数只能返回一个值，但可以使用元组或结构体等复合类型来返回多个值。

```rust
fn add_and_multiply(a: i32, b: i32) -> (i32, i32) {
    (a + b, a * b)
}

fn main() {
    let (sum, product) = add_and_multiply(2, 3);
    println!("sum = {}, product = {}", sum, product);
}
```

在这个例子中，add_and_multiply 函数返回由两个 i32 值组成的元组 (i32, i32)。

Rust 中的函数还可以使用 return 关键字来提前返回并提供函数的返回值。在这种情况下，必须指定返回的类型：

```rust
fn add(a: i32, b: i32) -> i32 {
    return a + b;
}

fn main() {
    let sum = add(2, 3);
    println!("sum = {}", sum);
}
```

在这个例子中，add 函数使用 return 关键字来提前返回并提供结果 a + b。由于此函数的返回类型指定为 i32，因此 return 关键字必须在值后面提供 i32 类型的结果。

注意，如果您使用 return 关键字提前返回，那么在其下方的所有代码都不会执行。也就是说，return 是一个跳转指令，它将控制流程移动到函数的最后一行并返回值。
