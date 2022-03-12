
1. 内核设置

1.1 内核需要开启支持bluetooth协议栈。

1.2 uart配置

	如果使用的是UART,内核中需要将对应的引脚配置成UART功能。

1.3 蓝牙驱动

	编译蓝牙驱动，生成的hci_uart.ko模块放到设备的对应目录module。

	rtk_hciattach工具放到对应的bin目录。

2. 蓝牙协议栈
	
2.1

	配置文件bluetooth.conf，system.conf放到指定目录中。

2.2

	dbus-deamon放到指定目录中。

2.3

	bluetoothd放到指定目录中。

3. 执行顺序：

```
insmod /usr/lib/modules/hci_uart.ko

rtk_hciattach -n -s 115200 ttyS3 rtk_h5 &

dbus-deamon --system

bluetoothd &
```

最后就可以调用bluetoothctl进行通信了。