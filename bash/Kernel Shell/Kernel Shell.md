# Kernel Shell

### UnKnow

```bash
sudo grep -i gpio /proc/iomem # 获取GPIO映射地址

```

![](image/image_4eoXQdG1-D.png)

```bash
pinout   # 显示引脚图
gpioinfo # 显示GPIO状态
modinfo  # 查看module信息
sudo cat /sys/kernel/debug/gpio # 查看gpio_pin_2对应的id位573
```

### pi-5

```bash
'修改启动顺序: 非必要不改, 不需要两个一起用'
sudo vi /boot/firmware/config.txt
  dtparam=pciex1  (启用PCIe, dtparam=pciex1_gen=3 启用PCIe_Gen3[不稳定]
sudo rpi-eeprom-config --edit

sudo vi /boot/firmware/cmdline.txt # 更改serial0(默认Debug串口)波特率, 更改之后等待重启完毕

# 更换内核出现问题: SD卡启动
sudo fdisk -l
sudo mount /dev/nvme0n1p1 /mnt # 不太清楚到底挂哪个,反正稀里糊涂的成功了
...修改...
sudo umount -v /dev/nvme0n1p1

```
