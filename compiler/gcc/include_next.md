# #include_next

## 使用准则

假设你在 `/usr/local/include` 中创建了一个新的 `stdio.h` 文件，希望在它里加入一些额外的调试信息，同时仍然保留系统的标准 `stdio.h`（通常位于 `/usr/include/stdio.h`）的所有功能。

> 在 `/usr/local/include/stdio.h` 中写入以下内容：

```c
#ifndef WRAPPER_STDIO_H
#define WRAPPER_STDIO_H

#include <stdio.h> // 递归包含问题

// 自定义代码
void debug_log(const char* message) {
    fprintf(stderr, "DEBUG: %s\n", message);
}

#endif // WRAPPER_STDIO_H
```

上述代码中的 `#include <stdio.h>` 试图引用系统的 `stdio.h`，但由于该文件自身并没有被多重包含保护，这种写法会导致递归包含的问题。为了避免无限递归，改用 `#include_next`:

```c
#ifndef WRAPPER_STDIO_H
#define WRAPPER_STDIO_H

#include_next <stdio.h> // 使用 #include_next 访问下一个 stdio.h

// 自定义代码
void debug_log(const char* message) {
    fprintf(stderr, "DEBUG: %s\n", message);
}

#endif // WRAPPER_STDIO_H
```

## 工作原理

当编译器在 `/usr/local/include/stdio.h` 中遇到 `#include_next <stdio.h>` 时，它会跳过当前目录继续查找下一个 `stdio.h` 

直至找到最后一个。接下来，编译器会在 `/usr/include/stdio.h` 中找到系统标准的 `stdio.h`，从而顺利包含标准库的定义。

