# 使用说明

ArchLinux 需要先安装 linux头文件

```
sudo pacman -S linux-headers
```

1. 打开“终端”
2. 切换到 “driver” 目录
3. 使用 “make” 编译驱动，成功会看到模块 “ch343.ko”
4. 输入 “sudo make load” 或 “sudo insmod ch343.ko” 动态加载驱动
5. 输入 “sudo make unload” 或 “sudo rmmod ch343.ko” 卸载驱动
6. 输入 “sudo make install” 使驱动程序永久工作
7. 输入 “sudo make uninstall” 删除驱动

# ch343 linux serial driver

## Description

​	USB to UART(s) chip ch342/ch343/ch344/ch347/ch9101/ch9102/ch9103/ch9143 are fully compliant to the  Communications Device Class (CDC) standard, they will work with a standard CDC-ACM driver (CDC - Abstract Control Model). Linux operating systems supply a default CDC-ACM driver that can be used with these USB UART devices. In Linux, this driver file name is cdc-acm.

​	The CDC-ACM driver has limited capabilities to control specific devices. This generic driver does not have any knowledge about specific device protocols. Because of this, device manufacturers can create an alternate, or custom driver that is capable of accessing the device specific function sets, such as hardware flow control or GPIO functions.

​	If you use this VCP driver, please check that the CDC-ACM driver was not installed for the USB UART devices mentioned above. You can use command "ls /dev/ttyACM*" to confirm that, to remove the CDC-ACM driver, use command "rmmod cdc-acm".

​	This driver supports USB to single serial port chip ch343/ch9101/ch9102/ch9143, USB to dual serial ports chip ch342/ch347/ch9103, USB to quad serial ports chip ch344, etc.

1. Open "Terminal"
2. Switch to "driver" directory
3. Compile the driver using "make", you will see the module "ch343.ko" if successful
4. Type "sudo make load" or "sudo insmod ch343.ko" to load the driver dynamically
5. Type "sudo make unload" or "sudo rmmod ch343.ko" to unload the driver
6. Type "sudo make install" to make the driver work permanently
7. Type "sudo make uninstall" to remove the driver
8. You can refer to the link below to acquire uart application, you can use gcc or Cross-compile with cross-gcc
   https://github.com/WCHSoftGroup/tty_uart

​	Before the driver works, you should make sure that the usb device has been plugged in and is working properly, you can use shell command "lsusb" or "dmesg" to confirm that, USB VID of these devices are [1A86], you can view all IDs from the id table which defined in "ch343.c".

​	If the device works well, the driver will created tty devices named "ttyCH343USBx" in /dev directory.

## Note

​	Any question, you can send feedback to mail: tech@wch.cn