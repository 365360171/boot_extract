## 1.进入 TWRP 终端命令

TWRP 终端自带 root 权限，故省略提权 `su` 命令。

## 2.查找内核分区位置

首先要查找内核分区所在位置，首先查找快捷方式，我们进入 /dev/block 目录下 by-name 文件夹。输入命令：

`cd /dev/block/by-name`

注意⚠️：不同手机系统可能不一样。目前 Google 标准 Android 分区是 /dev/block/by-name 。其他手机 by-name 可能在其他目录下。

## 3.查找内核真实地址

查找 boot 真实地址，输入命令：

`ls -l boot`

找到当前手机的 boot 地址，例如：/dev/block/sda11

## 4.提取内核分区为内核镜像

boot 地址为 /dev/block/sda11 ，所以使用 `dd` 命令提取保存即可：

`dd if=/dev/block/sda11 of=/sdcard/boot.img`