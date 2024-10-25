# WSL

```shell
" 压缩 "
wsl --shutdown
diskpart
select vdisk file = "C:\Users\Harvey\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu22.04LTS_79rhkp1fndgsc\LocalState\ext4.vhdx"
compact vdisk

" 删除 "
wsl -l
wsl --unregister <版本>

" 更换内核 "
wsl默认是分布式挂载，所以没有创建本地kernel
如果要使用本地kernel
在 %userprofile% 目录下添加 .wslconfig
内容为：

[wsl2]
kernel=C:\\Path\\To\\Kernel  
# 指定内核路径，我改成了C:\\Windows\\System32\\lxss\\tools\\kernel
# C:\Windows\System32\lxss\tools

然后把编译好的镜像（x86_64是bzImage）改名为kernel，放到设置的内核路径
```



# 理想Linux内核/虚拟化专家

- 精通ARM体系结构，有多核架构经验
- 精通Linux内核（对系统调度、内存管理、虚拟化有深刻的理解）
- 5年以上Linux内核/虚拟化相关开发经验
- 熟悉调试工具、底层库
- 熟悉硬件知识，具备良好的软硬件协同开发经验
