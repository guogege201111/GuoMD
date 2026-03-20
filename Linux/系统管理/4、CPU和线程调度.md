jetson系统最好将PCIE和usb中断限制在0-3

1、将线程绑定到cpu,需要写在线程函数开头,已经moveto线程并重复调用的函数绑定一次就行
```cpp
int bindThreadToCpu(int cpuId)
{
    cpu_set_t mask;
    CPU_ZERO(&mask);
    CPU_SET(cpuId, &mask);
    pthread_t thread = pthread_self();
    int ret = pthread_setaffinity_np(thread, sizeof(mask), &mask);
    return ret;
}
```

2、禁用系统默认调度
```
1）常规linux：

a、sudo nano /etc/default/grub

b、GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"改为              GRUB_CMDLINE_LINUX_DEFAULT="quiet splash isolcpus=1,2"

c、sudo update-grub
d、sudo reboot

e、执行cat /proc/cmdline，如果看到isolcpus=1,2则说明成功

f、取消隔离则删掉配置中的isolcpus=1,2并重复 cd


2）jetson系统
a、sudo nano /boot/extlinux/extlinux.conf

b、APPEND ${cbootargs} quiet splash改为APPEND ${cbootargs} quiet splash isolcpus=1,2

c、sudo reboot

```