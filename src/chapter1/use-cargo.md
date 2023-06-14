## 使用cargo run快速尝试代码

cargo run命令编译并运行源文件，而不将可执行文件保存到当前目录。它非常适合快速尝试简单的程序。让我们用它来运行示例。

使用Cargo创建一个Crate并运行的步骤如下：

1. 打开终端或命令行窗口，进入到你希望创建Crate的目录中。
2. 运行cargo new <crate-name>命令，其中<crate-name>是Crate的名称。例如，cargo new hello-world会在当前目录中创建一个名为hello-world的Crate。
3. 进入到新创建的Crate目录中：cd hello-world。
4. 编辑src/main.rs文件，这是Crate的入口文件。将以下代码复制并粘贴到该文件中：
    ```rust
    fn main() {
        println!("Hello, Rust!");
    }
    ```

5. 保存main.rs文件。
6. 在终端或命令行窗口中，使用cargo run命令来构建并运行Crate

    ```bash
    cargo run
    ```

你将立即看到程序输出。如果对源代码进行更改，则不必执行单独的编译步骤，只需使用cargo run运行代码，即可立即看到结果。当你在处理小程序时，cargo run是一个很方便的工具！
