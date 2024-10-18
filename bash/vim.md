# VIM

```vim&#x20;script
          --- l --->              
          | k
        j |   
 <--- h ---
```

```vim&#x20;script
w     # 下一个单词头
e     #          尾

H     # 当前屏幕 - 顶行
M     #           中行
L     #           底行

gg    :1     [[    1G    # 第一行
G     :$     ]]          # 最后一行

vi Makefile +1           # 定位到第一行
vi Makefile +$           # 定位到最后一行

{      # 段前
}      # 段后

$      # 行末
0      # 行首

-      # 上一行行首
+      # 下一行行首

123 <Enter>    # 向下移动 123行
<ctrl> d       # 向下移动  半页
<ctrl> f       #          一页
<ctrl> u       # 向上移动  半页
<ctrl> b       #          一页
```

```vim&#x20;script
<ctrl> 6       # 切回刚刚打开的文件

:b<number>     # :b6 跳到(已经打开的)第6个文件
:bn            # 跳到下一个文件
:bp            # 跳到上一个文件

:e <filename>  # 跳到<filename>文件
```

```vim&#x20;script
i          # 在前面插入
a          # 在后面

I          # 在行首插入
A          # 在行末插入

D     dd   # 删除
u          # 撤销

>>    # 缩进
<<
```

```vim&#x20;script
/菜需鲲               // 向前寻找  菜需鲲 
?菜需鲲               // 向前寻找  菜需鲲 

#                    // 如: 光标在ord单词及其前面的空格处, 使用#向前寻找相同的单词
*                    // 向后

:s/<old>/<new>       // 当前行
:1,100s/<old>/<new>  // 1~100行替换
:%s/<old>/<new>      // old替换成new(全局
:g/<old>/<new>
```

```vim&#x20;script
y      # 复制当前行
10y  # 从当前行的下一行开始, 复制后10行
v进入可视化模式, 上下移动选中文字, 然后y复制 

p      # 粘贴
```

```vim&#x20;script
ZZ     # :wq
ZQ     # :q
```

```vim&#x20;script
# 执行shell命令
:!<命令>   # 如 :!find arch/arm/asm -name 'page'

# 终端
:terminal # 在上方打开terminal
    :ter
:botright terminal # 在下方打开...
    :bo ter
# 退出exit就行
```
