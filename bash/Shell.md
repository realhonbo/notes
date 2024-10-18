# Shell

## 系统

```bash
uname -a  
# Linux ubuntu 5.4.0-1081-raspi #92-Ubuntu SMP PREEMPT Thu Feb 16 10:59:38 UTC 2023 aarch64 aarch64 aarch64 GNU/Linux
cat /proc/version
# Linux version 5.4.0-1081-raspi (buildd@bos01-arm64-012) (gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1)) #92-Ubuntu SMP PREEMPT Thu Feb 16 10:59:38 UTC 2023
screenfetch
# 有ubuntu标志的
sudo lscpu
sudo lshw

"包"
sudo apt-cache search aarch64  # 查看和aarch64相关的软件包
sudo dpkg -i xx.deb # 安装软件包

```

## 进程相关

```bash
" 进程 "
ps c     # 精简地显示所有进程
pstree   # 树状结构
ps cux   # 精简的显示进程信息
ps <pid>
'  STAT状态如下
D    uninterruptible sleep (usually IO)
I    Idle kernel thread
R    running or runnable (on run queue)
S    interruptible sleep (waiting for an event to complete)
T    stopped by job control signal
t    stopped by debugger during the tracing
W    paging (not valid since the 2.6.xx kernel)
X    dead (should never be seen)
Z    defunct ("zombie") process, terminated but not reaped by its parent
'

top      # 实时CPU进程状态
btop  # 图形监控台(实时) - top升级版
kill -9 <PID>   # 强制关闭进程

" 内存 "
free -h  # 查看内存占用
vmstat -s
cat /proc/meminfo  # 查看详细内存信息（上至总内存，下至内核栈）

```

## 文件

```bash
ls -d /etc/mod* # 列出/etc目录下的所有 以mod开头的文件(夹)

du -sh <file>  # 显示文件大小
sort -h  # 从小到大排序   -r ： 反转
uniq  # 去除相邻且相同的，一般和sort一起用
       # sort -c 统计每项相同个数
       # sort -i 忽略大小写
du -sh * | sort -h # 从小到大排序显示

ll -h          # 以kb模式显式

grep <obj> <file/dir> # 寻找<obj>字符
grep -r "字符" .  # 递归地查找字符， “.”代表当前文件夹（可省略）
grep -rl "字符" . # 查找包含字符的文件
grep -r --include="*.c" "字符" . # 在所有.c文件中查找

wc -l          # 统计数量
    # grep a 1.txt | wc -l

find <dir> -name '<file>' # 当前文件夹下寻找<file>文件(best!)
    # <dir>可缺省
    find -name "Image" | xargs du -sh
    # 26M     ./arch/arm64/boot/Image
    cd `find -name "boot" | head -n 1`
    cd $(...)
    cd `find -name "Image" -type f -exec dirname {} \;` # 去Image所在目录
dirname
    # find -name "<name>" | xargs dirname

rm -r !(*.c|*.o)  # 除了c/o其他的都删除
```

## 网络

```bash
# ubuntu24以下
" 查看wifi "
nmcli dev wifi
" 查看网卡 "
nmcli device
" 连接wifi "
sudo nmcli dev wifi connect Linux01 password mmmmmmmm (wep-key-type key ifname wlan0)
# ubuntu24以上
sudo vi /etc/netplan/<一个yaml文件>.yaml # 50-cloud-init.yaml
>>> 文件内容改为:
network:
    version: 2
    wifis:
        renderer: networkd
        wlan0:
            access-points:
                "未知网络":
                    password: "QWER147258369@"
            dhcp4: true
            optional: true
netplan try # 按Enter结束
netplan apply
---------------固定ip版本--------------------
network:
    version: 2
    wifis:
        renderer: networkd
        wlan0:
            access-points:
                "未知网络":
                    password: "QWER147258369@"
            dhcp4: false
            addresses: [192.168.10.158/24]
            routes:
              - to: default
                via: 192.168.1.1
                metric: 100
                on-link: true
            nameservers:
                addresses:
                  - 192.168.1.1
            optional: true


" 监视流量 "
bmon  # 监视网络上下行

" 查看ip "
ip addr (Ubuntu 24.04)

" 网络测试 "
nc <IP> <Port>
# windows建议用telnet替代，而不是nmap：
telnet <IP> <Port>

" 文件传输 "
scp -r tools/ boboo@192.168.10.158:/home/boboo # tools下的全部文件传输到rpi-5
scp -r boboo@192.168.10.158:~/dht22_driver A:/ # 将树莓派上的文件夹放入A盘
scp -r boboo@192.168.10.158:~/dht22_driver ~/  # 在主机而非树莓派上操作!

python -m http.server 8080 # 打开端口供Host访问(在vscode中使用,xterm普遍存在问题

"remote"
ssh-keygen -t rsa -b 4096
echo "<获取到的密匙>" >> ~/.ssh/authorized_keys

```

![](image/image_8rAXhka-si.png)

## Makefile调用

```makefile
$(shell <命令>)
$(shell pwd)
$(shell uname -r)

$(dir <file>)  ; 获取file的目录
include_path = $(foreach item,$(dirs), -I$(item)) ; 把dirs改成-Idirs，里面的每一项
```
