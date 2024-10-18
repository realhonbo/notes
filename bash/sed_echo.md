# Sed 与 echo

### sed

```bash
sed [param] [action] <file>

[param] :
  -i   直接修改读取的文件内容, 而不是输出到终端
  -n   只列出经过sed处理的行

[action] :
   a   新增
   d   删除
   i   插入
   c   行取代
   s   字符串替换

sed -i '1d' <file>  # 修改<file>, 删除第1行
sed -i '1a 东西' <file>  # 往第1行后面(第2行)添加'东西'
sed -i 's/原string/新string/g' <file>
  sed -i '1,20s/原string/新string/g' <file> # 1~20行内..
  sed -i 's/^@//' <file> # 去掉行首的@
  sed -i '/string/i 新string' <file> # string所在行前插入一行,内容为'新string'
  sed -i '/string/d' <file> # 删除string

# sed 不可以处理空文件 (如果需要, 请先 : echo "" >> <file> )
```

### echo

```bash
echo ' @$#%^&*()?|\./' >> myfile   # echo将单引号里面的 @$#%^&*()?|\./原封不动地写入myfile
echo " @$#%^&*()?|\./" >> myfile   # echo会解析双引号内的特殊符号

# echo一次只能写入一行, 没有换行输入
```
