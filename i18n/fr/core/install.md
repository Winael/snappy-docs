---
title: Installer snapd
language: French
---

### Arch

```
sudo pacman -S snapd
```

### Debian

```
# Sur Sid:
sudo apt install snapd
```

### Fedora

```
sudo dnf copr enable zyga/snapcore
sudo dnf install snapd

# activer le service snapd dans systemd :
sudo systemctl enable --now snapd.service

# Le support de SELinux support est en bêta, donc pour le moment :
sudo setenforce 0

# pour le rendre persistant, editez le fichier /etc/selinux/config
pour paramétrer SELINUX=permissive et derémarrez.
```

### Gentoo

Installation [snap-confine.ebuild](https://github.com/zyga/snap-confine-gentoo) et [snapd.ebuild](https://github.com/zyga/snapd-gentoo)

```
# activer le service snapd dans systemd :
sudo systemctl enable --now snapd.service
```

### OpenEmbedded/Yocto

Installer la [méta couche snap ](https://github.com/morphis/meta-snappy/blob/master/README.md).

### OpenSuse

```
sudo zypper addrepo http://download.opensuse.org/repositories/system:/snappy/openSUSE_Leap_42.2/ snappy
sudo zypper install snapd
```

### OpenWrt

Activer le [flux snap-openwrt](https://github.com/teknoraver/snap-openwrt/blob/master/README.md).

### Ubuntu

```
sudo apt install snapd
```
