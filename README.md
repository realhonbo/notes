# Notes
***
# Architectures
## ARM

- [ARM基础概念与常用语法](arch/arm/basic.md)
- [ARM64 的一些基本概念](arch/arm64/basic.md)

# Computer Science
- [Cache](computer_science/cache.md)
- [浮点数](computer_science/float.md)

# Shell

- [Bash 常用语法](shell/bash.md)
- [Git 常用语法](shell/git.md)
- [vim 操作](shell/vim.md)

# Tools

- [C/C++ 偏门语法](tools/c_c++.md)
- [CMakeList 常用语法](tools/CMakeLists.md)
- [Makefile 常用语法](tools/Makefile.md)
- [暂未归类的项](tools/other.md)

# Kernel

- [Bottom Half 下半部](kernel/Bottom_Half.md)
- [时间和定时器](kernel/time.md)
- [虚拟文件系统（VFS）](kernel/vfs.md)
- [页缓存和页回写](kernel/page_cache.md)
- [块I/O层（BIO）](kernel/bio.md)
- [设备模型](kernel/dev_model.md)
- [Linux 图形](kernel/graphic/Linux-Graphic.md)
- [中断](kernel/irq.md)
- [x86 内核栈](kernel/stack_x86-64.md)
- [NMI](kernel/nmi/nmi.md)
- [IPI - x86](kernel/ipi.md)
- [Kexec](kernel/kexec.md)
- [Kexec - x86](kernel/kexec_x86.md)
- [Kdump](kernel/kdump.md)
- [MCE](kernel/mce.md)
- [内核线程及 Stop Machine](kernel/stop_machine.md)
- [CPU 热插拔](kernel/cpu_hotplug.md)

## 锁
- [锁的基本知识](kernel/lock/Lock-1.md)
- [Linux 自旋锁的实现](kernel/lock/Lock-2-Linux_x86_Spin_Lock.md)
- [Linux 信号量（Semaphore）的实现](kernel/lock/Lock-3-Linux_Semaphore.md)
- [Linux Mutex 的实现](kernel/lock/Lock-4-Linux_Mutex.md)
- [自旋锁的新实现 - qspinlock](kernel/lock/qspinlock.md)
- [乐观自旋锁 osq_lock 的实现](kernel/lock/osq_lock.md)

## 进程调度
- [进程调度](kernel/sched/sched_intro.md)
- [UNIX进程调度](kernel/sched/sched_unix.md)
- [Linux进程调度（Linux Process Scheduling）](kernel/sched/sched_linux.md)
- [完全公平调度（Completely Fair Scheduler）](kernel/sched/sched_cfs.md)
- [CFS - 1](kernel/sched/sched_cfs-1.md)
- [实时调度](kernel/sched/sched_rt.md)
- [实时调度负载均衡](kernel/sched/sched_rt_load_balance.md)
- [内核抢占](kernel/sched/sched_kernel_preempt.md)

## 内存管理
- [内存管理](kernel/mm/mm.md)
- [分页管理](kernel/mm/mm_pagetable.md)
- [进程地址空间](kernel/mm/mm-1-process_addr_spc.md)
- [slab](kernel/mm/slab.md)
- [slub](kernel/mm/slub.md)
- [学习 /proc/meminfo](kernel/mm/meminfo.md)
- [内核中的直接映射](kernel/mm/direct_map.md)
- [缺页处理](kernel/mm/fault.md)
- [Folio](kernel/mm/folio.md)
- [Vmalloc](kernel/mm/vmalloc.md)

## 网络
- [Monitoring and Tuning the Linux Networking Stack: Receiving Data](kernel/networking/monitoring-tuning-linux-networking-stack-receiving-data.md)
- [TCP](kernel/networking/TCP.md)
- [macvlan](kernel/networking/macvlan.md)
- [ARP](kernel/networking/arp.md)
- [GARP](kernel/networking/garp.md)

### Netfilter
- [netfilter](kernel/networking/netfilter/netfilter.md)
- [conntrack](kernel/networking/netfilter/conntrack.md)

## 初始化
- [initcall](kernel/init/initcall.md)

## 性能诊断
- [Perf](kernel/profiling/perf.md)

## 跟踪
- [Ftrace](kernel/trace/ftrace.md)
- [Ftrace设计](kernel/trace/ftrace-design.md)

## 调试
- [Debug](kernel/debug/debug.md)
- [kprobes](kernel/debug/kprobes.md)

## 主题
- [KPTI](kernel/issues/kpti/kpti.md)
