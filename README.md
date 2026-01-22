# cloud-infra-linux
linux learning notes

# Linux Mint 安装 & 配置笔记（2026 年 1 月）

## 1. 用 U 盘安装 Linux Mint（Dell Latitude 5320）

- ISO Download: https://www.linuxmint.com/download.php
- Burn this to a USB Stick with Etcher:  https://etcher.balena.io/#download-etcher
- BIOS 设置：F2 进 BIOS → Secure Boot Disabled、Fast Boot Disabled、Boot Mode UEFI
- 启动菜单：F12 → 选 USB (带 UEFI 的那个)

## 2. 分区方案（手动分区推荐）

- /boot/efi：512MB，fat32，esp + boot 标志
- / ：60GB，ext4（系统 + 软件）
- swap：8GB（或等于内存）
- /home：剩余全部，ext4（不格式化，保留个人文件）

## 3. 设置开机需要密码（禁用自动登录）

### 图形方式：
菜单 → Login Window → Users → 关闭 Automatic Login

### 命令方式：
```bash
sudo nano /etc/lightdm/lightdm.conf

[Seat:*]
autologin-user=
autologin-user-timeout=0

关键：autologin-user= 后面留空（删除原来的用户名，如原来是 autologin-user=craig 就改成 autologin-user=）
	•  如果整段不存在，直接在文件末尾添加上面三行即可。
