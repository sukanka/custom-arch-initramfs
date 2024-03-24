# 自定义 archlinux initramfs

## 获取 ISO
```

```

解压 iso
拿到 initramfs 并解压
```
lsinitcpio -x initramfs-linux.img
```

## HTTP HOOK
```
git clone https://gitlab.archlinux.org/archlinux/mkinitcpio/mkinitcpio-archiso.git
```

## 启动命令
```
qemu-system-x86_64 \
-m 8G \
-net nic -net user -nographic \
-device nec-usb-xhci,id=xhci,addr=0x1b \
-device usb-tablet,id=tablet,bus=xhci.0,port=1 \
-device usb-kbd,id=keyboard,bus=xhci.0,port=2 \
-smp 4,cores=4  -kernel vmlinuz-linux  -initrd initramfs-linux.img -append 'archisobasedir=arch archiso_http_srv=http://192.168.122.1/  ip=dhcp console=ttyS0 '
```
