# Grammer

```cmake
set(CMAKE_CXX_STANDARD 17)

# clangd
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
bear -- gcc <filename> # 单个文件clangd

# 保存编译的中间文件
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -save-temps=obj")
```

# UFtrace

```cmake
add_compile_options(-pg)
```

```bash
uftrace record <exec>
  uftrace report
  uftrace graph
uftrace dump --flame-graph | ./flamegraph.pl > output.svg # .svg用chrome打开
```

