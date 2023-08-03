---
title: "Note per troubleshooting"
date: 2022-04-11
tags:
    - "Troubleshooting"
draft: false
langs: ["Italian", "English"]
---

# Introduzione
Qui mettero delle note personali per evitare di ritrovarmi sempre con gli stessi problemi (principalmente arch linux).

# Config

## Wireless

### Bluetooth

##### coexistence modules
This solve some glitches with bluetooth headphones.

[wiki.archlinux.org/title/Network_configuration/Wireless#Bluetooth_coexistence](https://wiki.archlinux.org/title/Network_configuration/Wireless#Bluetooth_coexistence)

`/etc/modprobe.d/iwlwifi.conf`
```
options iwlwifi bt_coex_active=0
```

## Networking

### Fail2ban
[wiki.archlinux.org/title/Fail2ban](https://wiki.archlinux.org/title/Fail2ban)

`sudo systemctl enable fail2ban.service`

#### SSH ban
[www.linode.com/docs/guides/how-to-use-fail2ban-for-ssh-brute-force-protection/](https://www.linode.com/docs/guides/how-to-use-fail2ban-for-ssh-brute-force-protection/)

`/etc/fail2ban/jail.local`
```
[sshd]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
findtime = 300
bantime = 3600
ignoreip = 127.0.0.1
```

### SSH multi-port disable password
[unix.stackexchange.com/questions/128444/disable-ssh-password-authentication-on-specific-interface](https://unix.stackexchange.com/questions/128444/disable-ssh-password-authentication-on-specific-interface)
`/etc/ssh/sshd_config`
```
Port 22
Port 2222
...
PasswordAuthentication no
Match address 192.168.213.0/24
	PasswordAuthentication yes
```

## Udiskie2 mount password
[gist.github.com/grawity/3886114#file-udisks2-allow-mount-internal-js](https://gist.github.com/grawity/3886114#file-udisks2-allow-mount-internal-js)
`/etc/polkit-1/rules.d/60-udiskie.rules`
```
polkit.addRule(function(action, subject) {
  var YES = polkit.Result.YES;
  var permission = {
    // required for udisks1:
    //"org.freedesktop.udisks.filesystem-mount": YES,
    "org.freedesktop.udisks.filesystem-mount-system-internal": YES,
    //"org.freedesktop.udisks.luks-unlock": YES,
    //"org.freedesktop.udisks.drive-eject": YES,
    "org.freedesktop.udisks.drive-detach": YES,
    // required for udisks2:
    //"org.freedesktop.udisks2.filesystem-mount": YES,
    "org.freedesktop.udisks2.filesystem-mount-system": YES,
    //"org.freedesktop.udisks2.encrypted-unlock": YES,
    //"org.freedesktop.udisks2.eject-media": YES,
    //"org.freedesktop.udisks2.power-off-drive": YES,
    // required for udisks2 if using udiskie from another seat (e.g. systemd):
    //"org.freedesktop.udisks2.filesystem-mount-other-seat": YES,
    //"org.freedesktop.udisks2.filesystem-unmount-others": YES,
    //"org.freedesktop.udisks2.encrypted-unlock-other-seat": YES,
    //"org.freedesktop.udisks2.eject-media-other-seat": YES,
    //"org.freedesktop.udisks2.power-off-drive-other-seat": YES
  };
  if (subject.isInGroup("storage")) {
    return permission[action.id];
  }
});
```

## Pacman

### Beauty things
`/etc/pacman.conf`
```
Color
VerbosePkgLists
ILoveCandy
```

### Parallel downloads
`/etc/pacman.conf`
```
ParallelDownloads = 15
```

### Arch news hook
[github.com/bradford-smith94/informant](https://github.com/bradford-smith94/informant)

AUR package: `informant`

## Pipewire

### Disable power save
To prevent pops when music starts.

```bash
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```

To make it permanent add to `/etc/modprobe.d/audio_disable_powersave.conf`:
```
options snd_hda_intel power_save=0
```

## Fish Shell

### Ctrl+Backspace kill word
```bash
bind \b backward-kill-word
```

### Remove fish greeting
```bash
set -U fish_greeting ""
```

# Kernel

## Sysrq
`echo "kernel.sysrq = 1" >> /etc/sysctl.d/99-sysctl.conf`

# Bootloader

## rEFInd

### Themes

- [github.com/bobafetthotmail/refind-theme-regular](https://github.com/bobafetthotmail/refind-theme-regular)

# Installation
[wiki.archlinux.org/title/Installation_guide](https://wiki.archlinux.org/title/Installation_guide)

## Partitioning
[wiki.archlinux.org/title/Partitioning](https://wiki.archlinux.org/title/Partitioning)

### LVM
[wiki.archlinux.org/title/LVM](https://wiki.archlinux.org/title/LVM)

### Resizing with filesystem
`lvresize -L +10G --resizefs MyVolGroup/mediavol`

`lvresize -L 15G --resizefs MyVolGroup/mediavol`

`lvresize -l +100%FREE --resizefs MyVolGroup/mediavol`

## Checklist
- `loadkeys colemak`
- `iwctl`
- `timedatectl set-ntp true`
- `fdisk`
- `mkfs.ext4`/`mkfs.fat -F 32`/`mkswap`
- `mount`/`swapon`
- `pacstrap /mnt base linux-zen linux-firmware base-devel nano micro neovim sudo man-db man-pages texinfo neofetch`
- `genfstab -U /mnt >> /mnt/etc/fstab`
- `arch-chroot /mnt`
- `ln -sf /usr/share/zoneinfo/Europe/Rome /etc/localtime`
- `hwclock --systohc`
- `micro /etc/locale.gen`
- `locale-gen`
- `micro /etc/locale.conf` -> `LANG=en_US.UTF-8`
- `micro /etc/vconsole.conf` -> `KEYMAP=colemak`
- `micro /etc/hostname` -> _`my hostname`_
- `mkinitcpio -P`
- `passwd`
- Install bootloader
- `useradd` (TODO)

# Utilities
## Sync
To view progress of sync command:

```
watch -d grep -e Dirty: -e Writeback: /proc/meminfo
```

[unix.stackexchange.com/questions/48235/can-i-watch-the-progress-of-a-sync-operation](https://unix.stackexchange.com/questions/48235/can-i-watch-the-progress-of-a-sync-operation)

# VirtualBox
## Import OVA
```
VBoxManage import KaliTraining.ova
```

# Gnome
## Alt-tab behavior
[superuser.com/questions/394376/how-to-prevent-gnome-shells-alttab-from-grouping-windows-from-similar-apps](https://superuser.com/questions/394376/how-to-prevent-gnome-shells-alttab-from-grouping-windows-from-similar-apps)

- Change alt-tab keybing from switch-application to switch-windows
- Open `dconf-editor`
- Uncheck `org/gnome/shell/window-switcher/current-workspace-only`

# BTRFS

## btrbk snapshots (fedora)
[mutschler.dev/linux/fedora-btrfs-35/](https://mutschler.dev/linux/fedora-btrfs-35/)
`/etc/btrbk/btrbk.conf`
```
transaction_log         /var/log/btrbk.log
lockfile                /var/lock/btrbk.lock
timestamp_format        long

snapshot_dir            _btrbk_snap
snapshot_preserve_min   3h
snapshot_preserve       6h 5d 3w 1m

volume /
  snapshot_create  always
  subvolume /
  subvolume home
```

`/lib/systemd/system/btrbk.timer`
```
[Unit]
Description=btrbk hourly backup

[Timer]
OnCalendar=hourly
AccuracySec=10min
Persistent=true

[Install]
WantedBy=timers.target
```

`sudo systemctl enable --now btrbk.timer`
