# gentoo--
纯小白傻瓜式安装😃

1.一个电脑
2.会打字的手
3.ubuntu镜像
4.一个U盘
5.下载一个rufus，或者是ventoy（直接制作不想多说😃）


开始安装！

从U盘启动。
开机选择U盘启动，把U盘插入USB口，开机疯狂按Delete进入BIOS，选择USB储存介质启动，进入刚刚制作的启动U盘。op0


联通网络。
Ubuntu联网大家都会吧应该。

硬盘分区。
首先打开终端，输入 sudo -i ，输入lsblk查看当前的电脑分区。这里使用cfdisk进行分区，输入 cfdisk /dev/sda 进行分区。
sda1    /efi    300m
sda2    /       100g
sda3    swap    8g

格式化分区。
首先格式化跟分区我用ext4 sda2
mkfs.ext4 -T small /dev/sda2
我是efi sda1 用FAT32
mkfs.vfat -F 32 /dev/sda1
激活swap分区
以下命令是初始化
mkswap /dev/sda3
以下命令是激活swap
swapon /dev/sda3

挂载root分区。
没什么好说的，直接看命令
mkdir --parents /mnt/gentoo
mount /dev/sda2 /mnt/gentoo
mkdir --parents /mnt/gentoo/efi
mount /dev/sda1 /mnt/gentoo/efi
如果/tmp/需要一个独立分区
chmod 1777 /mnt/gentoo/tmp

选择stage文件
我这里使用ustc
验证当前时间和日期（感觉不是很重要）
deta
stage文件的位置在（我这里选择openrc，当然你也可以选择systemd）:/gentoo/releases/amd64/autobuilds/current-stage3-amd64-desktop-openrc/(选择最新的下载)
我这里使用wget来下载
wget (刚刚复制的链接粘贴过来然后回车)
下载完后安装stage
tar xpvf stage3-*.tar.xz --xattrs-include＝'*.*' --numeric-owner





这里我使用了 gentoo官方文档做参考,还有yangmame的文章。
未完待续～   （懒得写了，放心，会继续写。）

注意:本人只是对gentoo感兴趣的纯小白，写的不好不要喷😰，感谢大家！
