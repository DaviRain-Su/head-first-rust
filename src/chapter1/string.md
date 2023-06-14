# 字符串

我们将字符串作为参数传递给println!。字符串是一系列字节，通常表示文本字符。你可以在代码中直接使用字符串字面量来定义字符串：双引号之间的文本，Rust将把它们视为字符串。

```bash
左双引号   "hello, Rust!"   右双引号

Output:
Hello, Rust!
```

在字符串中，换行符、制表符和其他难以包含在程序代码中的字符可以用转义序列来表示：反斜杠后跟表示另一个字符的字符。

```bash
1. "Hello, \nRust!"   字符串中的换行符

Output:
Hello,
Rust!

2. "Hello, \tRust!"

Output:
Hello,  Rust!

3. "Quotes: \"\""

Output:
Quotes: ""

4. "Backslash: \\"

Output:
Backslash: \
```

| 转移序列	| 值 |
| -------- | -- |
| \n | 	换行符 |
| \t | 	制表符 |
| \” | 	双引号 |
| \	 | 反斜杠 |
