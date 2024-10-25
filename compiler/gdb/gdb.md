# GDB

```bash
gcc < .cc> -g
# 向 <exec> 中插入 .debug_str .debug_line .debug_abbrev .debug_info .debug_aranges 等 section，保存调试信息

gdb <exec>  # 或者  gdb启动后指定文件--> (gdb)file/symbol-file <exec>

b <行/函数>  # break
    i b  查看所有断点
    disable 禁用所有
    enable  启用所有
    d <行/函数> 删除断点  # d 1-6

run  # run之后可以disassemble查看反汇编

c / n # continue / next

p <var> # print
    #调试寄存器
    info registers 或者 i r # 显示所有内核寄存器
    i r rx  # 显示rx的值
    i locals # 所有当前frame变量
    i args # 参数

watch <var> # 跟踪var的值

x <addr>  # 查看内存

list # 查看上下代码（多次list会连续向下显示）
  list -20 # 上20行
  list +20 # 下20行

set <var>=<new_val> # 强行更改变量的值

disassemble # 反汇编
  disassemble <func> # 把<func>/<addr>处反汇编
    disassemble /r <func> # 并且显示机器码
    disassemble /m <func> # 列出每行C代码对应的汇编码
  disassemble <start>, <end>
  disassemble <func>, +<lenth>
  

# 调试qemu (Linux0.11)
set arch i386:x86-64:intel

target remote localhost:1234

symbol-file  <tools/文件>
    # 等价于   file <tools/文件>

# in vscode debug console
-exec <instruction>

```

# OBJDUMP

```bash
objdump 
    -D  反汇编
    -b  指定文件格式 # -b binary 指定二进制格式
    -m  指定架构
    -d 指定被反汇编的文件（可以省略）
```

# KGDB

```bash
'获取modules代码段(bss段/数据段)的装载地址'
sudo cat /sys/module/dht22/sections/.text(.bss/.data)

# 指定输出串口
echo "ttyAMA10,921600" > /sys/module/kgdboc/parameters/kgdboc
# 启用 kgdb
echo g > /proc/sysrq-trigger
# 退出
go

# 单步调试       断点        sp指针   
ss            bp <addr>      bt
# 读寄存器     修改寄存器
rd            rm x9 0x0
# 读内存         修改内存
md <addr>    mm <addr> <val>

```

# FTrace

```bash
'设定函数跟踪器'
echo 0 > /sys/kernel/debug/tracing/tracing_on
echo "function_graph" > /sys/kernel/debug/tracing/current_tracer

'设定跟踪特定的函数' # 当然可以不设置，那样会跟踪所有能跟踪的函数
echo <function-name> > /sys/kernel/debug/tracing/set_ftrace_filter

'指定跟踪特定的CPU'
echo <cpu-id> > /sys/kernel/debug/tracing/tracing_cpumask

'开始跟踪'
echo 1 > /sys/kernel/debug/tracing/tracing_on
cat /sys/kernel/debug/tracing/trace_pipe | tee /tmp/ftrace.log

./<exec-name>

'关闭跟踪'
echo 0 > /sys/kernel/debug/tracing/tracing_on
echo nop > /sys/kernel/debug/tracing/current_tracer
# 注意, tracing_on只是关闭了一个开关, 将current_tracer设置为nop才能相对彻底地关闭动态跟踪
# mcount函数内容被替换成nop指令, 不再额外占用过多的 CPU 开销
'获取结果'
cat /sys/kernel/tracing/trace > ./trace_output
 https://github.com/freelancer-leon/notes/blob/master/kernel/trace/ftrace.md
```
