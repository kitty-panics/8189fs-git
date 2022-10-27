# 8189fs-git

[rtl8189fs] 驱动的 [AUR] [打包脚本]，相较于原版 [8189fs-git]，有以下改动。

- 方便在 x86 机器上通过 [chroot] 的方式打包。
- 以所用的 `以当前的内核版本为版号`

[rtl8189fs]: https://github.com/jwrdegoede/rtl8189ES_linux/tree/rtl8189fs
[AUR]: https://aur.archlinux.org/
[打包脚本]: https://wiki.archlinux.org/title/PKGBUILD
[8189fs-git]: https://aur.archlinux.org/packages/8189fs-git

## 在 x86 机器上编译

0. 取下 MicroSD 卡并通过读卡器插入到 x86 机器
1. `sudo sudo mount /dev/sdXY /mnt`
2. `sudo pacman -S qemu-user-static arch-install-scripts`
3. `sudo systemctl start systemd-binfmt.service`
4. `su --login --shell=/bin/bash`
5. `arch-chroot /mnt /bin/bash`
