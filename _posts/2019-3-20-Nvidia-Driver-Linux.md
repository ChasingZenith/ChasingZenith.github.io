---
layout: post
title:  "Nvidia Driver for Ubuntu"
date:   2019-3-20 20:25:20 +0800
categories: Linux Nvidia
---

apci_osi="Linux" nomodeset

sudo gedit /etc/modprobe.d/blacklist.conf

blacklist nouveau

sudo update-initramfs -u


重启之后，可以查看nouveau有没有运行:

lsmod | grep nouveau  # 没输出代表禁用生效

sudo apt install build-essential

sudo telinit 3


https://devtalk.nvidia.com/default/topic/1048439/linux/ubuntu-18-04-login-loop-after-driver-install-/post/5320913/#5320913

Please remove the kernel parameter 'nomodeset' 

Please run
grep modeset /etc/modprobe.d/* /lib/modprobe.d/*
to find the file containing
options nvidia-drm modeset=1
and change it to
options nvidia-drm modeset=0
then run
sudo update-initramfs -u
and reboot.
Also, run
sudo journactl -b0 --no-pager _COMM=gdm-x-session >journal.log
after trying to log in and attach that. 
