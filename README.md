<div align="center">
  <div>
      <a href="#readme">
        <img src="https://www.archlinux.org/static/logos/archlinux-logo-dark-1200dpi.b42bd35d5916.png" alt="Arch Logo" />
      </a>
  </div>
  <hr>
  <br>
  <div>
    <a href="https://github.com/D3S0X/arch-installation/">
      <img src="https://img.shields.io/github/last-commit/D3S0X/arch-installation.svg?style=for-the-badge&label=Last%20update" alt="Last Update" />
      <img src="https://img.shields.io/github/stars/D3S0X/arch-installation?style=for-the-badge" alt="Stars">
      <img src="https://img.shields.io/github/license/D3S0X/arch-installation?style=for-the-badge" alt="License">
    </a>
  </div>
</div>

## Index
- [0. Introduction](#0-introduction)
  - [Why this guide?](#why-this-guide)
  - [Important other resources](#important-other-resources)
- [1. Live Setup](#1-live-setup)
    - [Set keyboard layout](#set-keyboard-layout)
    - [If you use WiFi to connect to your router](#if-you-use-wifi-to-connect-to-your-router)
    - [Check internet connection](#check-internet-connection)
    - [Sync time](#sync-time)
    - [Check if booted in BIOS or UEFI](#check-if-booted-in-bios-or-uefi)
- [2. Partitioning + Formatting](#2-partitioning--formatting)
  - [Partitioning](#partitioning)
    - [List partition table](#list-partition-table)
    - [Start partitioning tool](#start-partitioning-tool)
    - [Create partitions](#create-partitions)
      - [Decide partition table type](#decide-partition-table-type)
      - [GPT (UEFI)](#gpt-uefi)
      - [DOS (BIOS)](#dos-bios)
      - [GPT (BIOS)](#gpt-bios)
    - [Size recommendations](#size-recommendations)
      - [EFI system](#efi-system)
      - [Swap](#swap)
  - [Format partitions](#format-partitions)
    - [EFI system partition](#efi-system-partition)
    - [Create root filesystem](#create-root-filesystem)
    - [Create home partition filesystem](#create-home-partition-filesystem)
    - [Create Swap](#create-swap)
- [3. Mount file systems](#3-mount-file-systems)
- [4. Base installation](#4-base-installation)
  - [Rank the mirrors before for faster downloads](#rank-the-mirrors-before-for-faster-downloads)
  - [Start the installation](#start-the-installation)
    - [Create filesystem table](#create-filesystem-table)
    - [Change root](#change-root)
- [5. Install Bootloader](#5-install-bootloader)
- [6. Configure system](#6-configure-system)
  - [The nano text editor](#the-nano-text-editor)
  - [Setup hostname](#setup-hostname)
  - [Setup locale](#setup-locale)
  - [Setup time & date](#setup-time--date)
  - [Configure pacman](#configure-pacman)
    - [Setup multilib](#setup-multilib)
    - [Extra candy](#extra-candy)
    - [After configuring](#after-configuring)
- [7. Setup users](#7-setup-users)
  - [Set root password](#set-root-password)
  - [Add your user](#add-your-user)
  - [Enable sudo](#enable-sudo)
- [8. Install Desktop](#8-install-desktop)
  - [Display Server](#display-server)
  - [Desktop Environment](#desktop-environment)
    - [KDE Plasma](#kde-plasma)
    - [Xfce](#xfce)
    - [GNOME](#gnome)
    - [LXDE](#lxde)
    - [LXQt](#lxqt)
    - [Cinnamon](#cinnamon)
    - [Budgie](#budgie)
    - [Mate](#mate)
    - [Deepin](#deepin)
  - [Display Manager (Desktop Manager)](#display-manager-desktop-manager)
    - [LXDM (Included in LXDE)](#lxdm-included-in-lxde)
    - [SDDM (Included in KDE Plasma)](#sddm-included-in-kde-plasma)
    - [GDM (Included with GNOME/Budgie/MATE)](#gdm-included-with-gnomebudgiemate)
    - [LightDM](#lightdm)
- [9. Useful packages](#9-useful-packages)
  - [General packages](#general-packages)
  - [Media Codecs](#media-codecs)
  - [Printer support](#printer-support)
    - [General packages](#general-packages-1)
    - [Qt Scan Application](#qt-scan-application)
    - [GTK Scan Application](#gtk-scan-application)
    - [UI for HP Printers](#ui-for-hp-printers)
  - [Bluetooth support](#bluetooth-support)
  - [Input Driver](#input-driver)
  - [Graphics Driver](#graphics-driver)
    - [Mesa](#mesa)
    - [Vulkan](#vulkan)
    - [Open Source drivers](#open-source-drivers)
    - [Nvidia proprietary driver](#nvidia-proprietary-driver)
    - [AMD Utils](#amd-utils)
    - [Intel Utils](#intel-utils)
    - [Gaming packages](#gaming-packages)
  - [Networking](#networking)
    - [If you use WiFi:](#if-you-use-wifi)
  - [Some archive and file system utils](#some-archive-and-file-system-utils)
  - [Sound](#sound)
  - [Other shells](#other-shells)
    - [zsh (Z Shell)](#zsh-z-shell)
    - [fish (Friendly interactive shell)](#fish-friendly-interactive-shell)
- [10. Reboot](#10-reboot)
- [11. Post installation](#11-post-installation)
  - [Set X11 Keymap](#set-x11-keymap)
  - [WiFi](#wifi)
  - [Oh My Zsh](#oh-my-zsh)
  - [Oh my Fish](#oh-my-fish)
  - [AUR Setup](#aur-setup)
  - [Yay Cheat sheet](#yay-cheat-sheet)
  - [Firefox for KDE Plasma](#firefox-for-kde-plasma)
  - [If you want a graphical package manager](#if-you-want-a-graphical-package-manager)
  - [If you use a GTK desktop and want Qt apps to use your GTK Theme](#if-you-use-a-gtk-desktop-and-want-qt-apps-to-use-your-gtk-theme)
  - [If you want to read APFS Partitions](#if-you-want-to-read-apfs-partitions)
  - [Graphics card configuration tool](#graphics-card-configuration-tool)
    - [AMD](#amd)
    - [NVIDIA](#nvidia)
  - [Fonts](#fonts)
    - [General Fonts](#general-fonts)
    - [Windows Fonts](#windows-fonts)
    - [macOS Fonts](#macos-fonts)
  - [Nano syntax highlighting](#nano-syntax-highlighting)
  - [Auto clean package cache](#auto-clean-package-cache)
  - [Theming](#theming)
    - [General](#general)
    - [Plasma & Qt](#plasma--qt)
    - [GTK & GNOME](#gtk--gnome)
- [12. Some fixes and tweaks](#12-some-fixes-and-tweaks)
  - [Compatibility tweaks](#compatibility-tweaks)
    - [Spotify local files](#spotify-local-files)
  - [Fix on shutdown "Failed to start user manager service for user 174" (sddm)](#fix-on-shutdown-failed-to-start-user-manager-service-for-user-174-sddm)
  - [Force Color Emoji](#force-color-emoji)
  - [Desktop icons for nemo](#desktop-icons-for-nemo)
  - [Backup / Restore](#backup--restore)
  - [System](#system)
  - [Packages / Services List](#packages--services-list)
    - [Backup](#backup)
    - [Restore](#restore)

# 0. Introduction

## Why this guide?
The Arch Wiki has these informations spread across multiple pages and I think this is much more clearly layed out and straight forward.
It also contains some packages and decisions that are personal preference.

## Important other resources

The Arch Wiki is a very powerful resource. If you have any problems it's the first place to search for solutions  
<https://wiki.archlinux.org>

Especially for the installation please read  
<https://wiki.archlinux.org/index.php/installation_guide>

Sometimes packages need manual intervention which is announced at  
<https://www.archlinux.org/news/>  
So keep an eye on it or ideally subscribe to the mailing list at  
<https://lists.archlinux.org/listinfo/arch-announce>

This tutorial is inspired by <https://sourceforge.net/projects/ezos/files/ArchStuff/> and have taken out some stuff of it

# 1. Live Setup

At this point, I assume you're already in the archiso.

### Set keyboard layout
⌨️ The default keymap is US. Available layouts can be listed with:
```
ls /usr/share/kbd/keymaps/**/*.map.gz
```
Set your keymap (replace `yourkeymap` with your keymap e.g. `de-latin1`)
```
loadkeys yourkeymap
```

### If you use WiFi to connect to your router
📶 Use this tool to connect to your network
```
wifi-menu
```

### Check internet connection
```
ping -c 3 archlinux.org
```

### Sync time
🕒 Ensure the system clock is accurate
```
timedatectl set-ntp true
```

### Check if booted in BIOS or UEFI
```
ls /sys/firmware/efi/efivars
```
If the directory does not exist, the system may be booted in Legacy BIOS Mode.
Most likely you want to do a UEFI install so please double check if your system supports UEFI and you selected the correct entry in the boot menu (In most cases prefixed with UEFI)

# 2. Partitioning + Formatting

> In the following X and Y are placeholders. Replace them with your corresponding device and partition number. "sd" could also be different if you don't connect your hard drive via SCSI/SATA

## Partitioning

### List partition table

To get an overview you can list your partition table to find out the device you want to use
```
fdisk -l
```

### Start partitioning tool
▶️ Text-based
```
fdisk /dev/sdX
```
▶️ UEFI only text-based
```
gdisk /dev/sdX
```
▶️ Graphical (Recommended for beginners)
```
cfdisk /dev/sdX
```
▶️ UEFI only Graphical (Recommended for beginners)
```
cgdisk /dev/sdX
```

### Create partitions

#### Decide partition table type
 - BIOS: You can use both but this guide uses DOS
 - UEFI: You need to use GPT

#### GPT (UEFI)

| Needed | Partition | Partition type       | Mount point   |
|--------|-----------|----------------------|---------------|
| ✔️      | /dev/sdXY | EFI system partition | /mnt/boot/efi |
| ❌      | /dev/sdXY | Linux swap           | -             |
| ✔️      | /dev/sdXY | Linux                | /mnt          |
| ❌      | /dev/sdXY | Linux                | /mnt/home     |

#### DOS (BIOS)

| Needed | Partition | Partition type | Mount point | Flags    |
|--------|-----------|----------------|-------------|----------|
| ❌      | /dev/sdXY | Linux swap     | -           | -        |
| ✔️      | /dev/sdXY | Linux          | /mnt        | Bootable |
| ❌      | /dev/sdXY | Linux          | /mnt/home   | -        |

#### GPT (BIOS)


### Size recommendations

#### EFI system
- At least: 150MB
- Recommended: 300MB

#### Swap

Taken from <https://docs.voidlinux.org/installation/live-images/partitions.html>

| System RAM | Recommended swap space | Swap space if using hibernation |
|------------|------------------------|---------------------------------|
| < 2GB      | 2x the amount of RAM   | 3x the amount of RAM            |
| 2-8GB      | Equal to amount of RAM | 2x the amount of RAM            |
| 8-64GB     | At least 4GB           | 1.5x the amount of RAM          |
| 64GB       | At least 4GB           | Hibernation not recommended     |

## Format partitions

### EFI system partition
```
mkfs.fat -F32 -n EFI /dev/sdXY
```

### Create root filesystem
💽 This will create the filesystem where the system will be installed on
```
mkfs.ext4 -L ROOT /dev/sdXY
```

### Create home partition filesystem
🏠 If you created a separate home partition
```
mkfs.ext4 -L HOME /dev/sdXY
```

### Create Swap
```
mkswap -L SWAP /dev/sdXY
swapon /dev/sdXY
```

# 3. Mount file systems
💽 Mount root filesystem:
```
mount /dev/sdXY /mnt
```

▶️ UEFI
```
mkdir -p /mnt/boot/efi
mount /dev/sdXY /mnt/boot/efi
```

🏠 If you created a separate home partiton:
```
mkdir /mnt/home
mount /dev/sdXY /mnt/home
```

# 4. Base installation

## Rank the mirrors before for faster downloads
📊 This will rank the mirrorlist. You may replace United States with your country
```
pacman -Sy archlinux-keyring reflector
reflector --country 'United States' --age 15 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
```

## Start the installation
⏳ This will install the system and may take a while
```
pacstrap /mnt base base-devel linux linux-firmware linux-lts sysfsutils usbutils e2fsprogs inetutils netctl nano less which man-db man-pages
```
> ⚠️ To ensure system stability append the microcode package for your CPU
> - `amd-ucode` for AMD CPUs
> - `intel-ucode` for Intel CPUs 
> - See <https://wiki.archlinux.org/index.php/Microcode>

### Create filesystem table
This will create the file system table which contains all the partitions and mountpoints
```
genfstab -U /mnt >> /mnt/etc/fstab
```

### Change root
After you entered this command you are basically in the installed system
```
arch-chroot /mnt
```

# 5. Install Bootloader
▶️ UEFI
```
pacman -S grub os-prober efibootmgr dosfstools mtools gptfdisk fatresize
grub-install --target=x86_64-efi --bootloader-id=grub_uefi --efi-directory=/boot/efi --recheck
grub-mkconfig -o /boot/grub/grub.cfg
```

▶️ BIOS
```
pacman -S grub os-prober
grub-install --target=i386-pc --recheck /dev/sdX
grub-mkconfig -o /boot/grub/grub.cfg
```

# 6. Configure system

## The nano text editor
Nano is the text editor we will use in this tutorial. Basic Usage:
- Move with arrow keys
- `CTRL + W` and then `ENTER` to save
- `CTRL + X` to exit

## Setup hostname
📛 This will be the name of your PC on your network  (Replace `myhostname`)
```
echo myhostname > /etc/hostname
nano /etc/hosts
```
Add these lines
```
127.0.0.1   localhost
::1         localhost
127.0.1.1   myhostname.localdomain  myhostname
```

## Setup locale
🌐 Uncomment (remove the # in front of) all languages you need
```
nano /etc/locale.gen
```
🏁 Generate locales
```
locale-gen
```
🔘 Set locale
```
echo LANG=en_US.UTF-8 > /etc/locale.conf
export LANG=en_US.UTF-8
```
⌨️ Set tty keymap (replace `yourkeymap` with your keymap e.g. `de-latin1`)
```
echo KEYMAP=yourkeymap > /etc/vconsole.conf
```

## Setup time & date

📅 You can tab-complete your stuff after zoneinfo
```
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
hwclock --systohc --utc
```

## Configure pacman

Edit pacman configuration file
```
nano /etc/pacman.conf
```

### Setup multilib
👾 multilib is a repository which contains 32-bit libraries and is disabled by default (needed for some games & software; highly recommended to enable)

💥 Uncomment (remove the # in front of) the following lines
```
[multilib]
Include = /etc/pacman.d/mirrorlist
```

### Extra candy
🍬 If you want some extra candy you can uncomment `Color` and `VerbosePkgLists` and add `ILoveCandy` under `Misc options`.

### After configuring
```
pacman -Syu
```

# 7. Setup users

## Set root password
🔑 Use a strong and complicated password
```
passwd
```

## Add your user
🧑 This will be your user you use to log in. For group reference see <https://wiki.archlinux.org/index.php/Users_and_groups#Group_list>
```
useradd -m -G users,wheel,sys,log,network,rfkill,lp,adm -s /bin/bash yourusername
passwd yourusername
```
🎰 If you want to force your user to change password after first login:
```
chage -d 0 yourusername
```

## Enable sudo
🧐 This will give your user administrative privileges
```
EDITOR=nano visudo
```
💥 Uncomment (remove the # in front of) the following lines
```
%wheel ALL=(ALL) ALL
```

# 8. Install Desktop

## Display Server
🖥️ Xorg is the display server we will use
```
pacman -S xorg-server xorg-xinit xorg-xrandr xorg-xfontsel xorg-xkill
```

## Desktop Environment

🗔 You need to select a desktop environment

- For beginners coming from Windows I recommend KDE Plasma.
- For a very resource friendy desktop I recommend Xfce or LXQt
- **The instructions for KDE Plasma are tested by me because I use it. Others should work but you may need some extra packages for productive use (pull requests are welcome)**

### KDE Plasma
```
pacman -S plasma kdialog packagekit-qt5 kcalc konsole dolphin kdegraphics-thumbnailers ffmpegthumbs kdenetwork-filesharing gwenview ark kate okular kcron kdf filelight print-manager
```
If you want to use KDE Connect (Pairing with Android phone)
```
pacman -S kdeconnect sshfs
```
See also <https://wiki.archlinux.org/index.php/KDE>
### Xfce
```
pacman -S xfce4 xfce4-goodies
```
See also <https://wiki.archlinux.org/index.php/Xfce>
### GNOME
```
pacman -S gnome gnome-extra
```
See also <https://wiki.archlinux.org/index.php/GNOME>
### LXDE
```
pacman -S lxde lxdm-gtk3
```
See also <https://wiki.archlinux.org/index.php/LXDE>
### LXQt
```
pacman -S lxqt breeze-icons pcmanfm-qt qterminal lxqt-sudo polkit-qt5
```
See also <https://wiki.archlinux.org/index.php/LXQt>
### Cinnamon
```
pacman -S cinnamon cinnamon-translations nemo-fileroller nemo-image-converter nemo-preview xed xreader gnome-terminal metacity gnome-shell
```
See also <https://wiki.archlinux.org/index.php/Cinnamon>
### Budgie
```
pacman -S budgie-desktop network-manager-applet gnome
```
See also <https://wiki.archlinux.org/index.php/Budgie>
### Mate
```
pacman -S mate mate-extra gdm
```
See also <https://wiki.archlinux.org/index.php/MATE>
### Deepin
```
pacman -S deepin deepin-extra
nano /etc/lightdm/lightdm.conf
greeter-session=lightdm-deepin-greeter
```
See also <https://wiki.archlinux.org/index.php/Deepin>

## Display Manager (Desktop Manager)
🖥️ A display manager is basically your login screen where you enter your user details and select your Desktop Environment

### LXDM (Included in LXDE)
```
pacman -S lxdm-gtk3
systemctl enable lxdm
```
See also <https://wiki.archlinux.org/index.php/LXDM>

### SDDM (Included in KDE Plasma)
```
pacman -S sddm
systemctl enable sddm
```
See also <https://wiki.archlinux.org/index.php/SDDM>

### GDM (Included with GNOME/Budgie/MATE)
```
pacman -S gdm
systemctl enable gdm
```
See also <https://wiki.archlinux.org/index.php/GDM>

### LightDM
```
pacman -S lightdm lightdm-gtk-greeter
systemctl enable lightdm
```
See also <https://wiki.archlinux.org/index.php/LightDM>

# 9. Useful packages

## General packages
```
pacman -S linux-headers linux-lts-headers dkms
pacman -S jshon expac git wget acpid avahi net-tools xdg-user-dirs
systemctl enable acpid avahi-daemon systemd-timesyncd
```

If system is running on a SSD
```
systemctl enable fstrim.timer
```

## Media Codecs
```
pacman -S gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi gst-transcoder x265 x264 lame
```

## Printer support
🖨️ Add some packages needed for printing and scanning
### General packages
```
pacman -S system-config-printer foomatic-db foomatic-db-engine gutenprint gsfonts cups cups-pdf cups-filters sane
systemctl enable org.cups.cupsd.service saned.socket
```
### Qt Scan Application
Use this if you use KDE Plasma or LXQt
```
pacman -S skanlite
```
### GTK Scan Application
Use this if you use another desktop environment
```
pacman -S simple-scan
```
### UI for HP Printers
🖨 Install this if you have a HP Printer
```
pacman -S hplip
```

## Bluetooth support
🔵 Add some packages needed for proper bluetooth support
```
pacman -S bluez bluez-utils
systemctl enable bluetooth
```

## Input Driver
These are some packages needed for certain input devices to properly work. It does no harm to install then, even if you wouldn't need them
```
pacman -S xf86-input-synaptics xf86-input-libinput xf86-input-evdev
```
When installing inside a virtual machine:
```
pacman -S xf86-input-vmmouse
```

## Graphics Driver

### Mesa
This is useful for all GPUs
```
pacman -S mesa lib32-mesa
```
### Vulkan
This is useful for all GPUs
```
pacman -S vulkan-icd-loader lib32-vulkan-icd-loader
```
### Open Source drivers
Only install this if you use an AMD or Intel GPU or want to use the open source NVIDIA driver (Nouveau, not developed by NVIDIA)
```
pacman -S <driver>
```
- `xf86-video-amdgpu` is for newer AMD GPUs
- `xf86-video-nouveau` is the open source NVIDIA driver
- `xf86-video-intel` is for intel GPUs
- `xf86-video-ati` is for older AMD GPUs
- `xf86-video-vmware` for VirtualBox, VMWare, QEMU
- `xf86-video-fbdev` for Hyper-V
- If you don't know it you can install all but it could happen that the internal graphics card is used if you install the driver for it

### Nvidia proprietary driver
Only install these packages if you are using a NVIDIA GPU
```
pacman -S nvidia nvidia-lts nvidia-utils lib32-nvidia-utils
```
### AMD Utils
Only install these packages if you are using an AMD GPU
```
pacman -S vulkan-radeon lib32-vulkan-radeon libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau amdvlk lib32-amdvlk
```
### Intel Utils
Only install this package if you are using an Intel GPU
```
pacman -S vulkan-intel
```
### Gaming packages
These packages are useful for gaming
```
pacman -S vkd3d lib32-vkd3d faudio lib32-faudio
```

## Networking
🖧 Those are essential networking tools
```
pacman -S networkmanager networkmanager-openvpn networkmanager-pptp networkmanager-vpnc
systemctl enable NetworkManager
```
### If you use WiFi:
📶 Those are essential tools if you connect to the internet via WiFi
```
pacman -S wireless_tools wpa_supplicant ifplugd dialog
```

## Some archive and file system utils
🗄️ Important tools for archives and file systems
```
pacman -S p7zip unrar unarchiver unzip unace xz rsync
pacman -S nfs-utils cifs-utils ntfs-3g exfat-utils
```

## Sound
🔊 Some essential packages for sound
```
pacman -S alsa-utils pulseaudio-alsa pulseaudio-equalizer
```
Control app for Qt Desktop (KDE Plasma or LXQt)
```
pacman -S pavucontrol-qt
```
Control app for GTK Desktop (another desktop environment)
```
pacman -S pavucontrol
```

🔇 PulseAudio fix notifications muting some media players
```
nano /etc/pulse/default.pa
```
💥 Comment (add # in front of) `# load-module module-role-cork`

## Other shells

🐚 You may want to use another shell than bash
### zsh (Z Shell)
```
pacman -S zsh zsh-completions
chsh -s /usr/bin/zsh yourusername
```
### fish (Friendly interactive shell)
```
pacman -S fish
chsh -s /usr/bin/fish yourusername
```

# 10. Reboot
```
exit
umount -R /mnt
telinit 6
```

# 11. Post installation

## Set X11 Keymap
⌨️ It's recommended to set this to your keymap. Some Display Manager and Desktop Environments use this (replace `yourkeymap` with your keymap e.g. `de-latin1`)
```
localectl set-x11-keymap yourkeymap
```

## WiFi
📶 You can use `nmtui` or `wifi-menu` to configure your network profile

## Oh My Zsh
🤖 A delightful & open source framework for Zsh
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Oh my Fish
🤖 The Fishshell Framework
```
curl -L https://get.oh-my.fish | fish
```

## AUR Setup
The Arch User Repository is a community-driven repository for Arch users. `yay` is a pacman wrapper that allows installing AUR packages
```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -rsi
cd .. && rm -rf yay
```
## Yay Cheat sheet
- `yay` Update system
- `yay xyz` Install xyz
- `yay -Rns xyz` Uninstall xyz
- `yay -Rdd xyz` Force remove xyz (should not be used)
- `yay -Yc` Uninstall not explicitly installed optional dependencies
- `yay -Si xyz` Show remote package
- `yay -Qi xyz` Show local package
- `yay -Qq` List installed packages
- `yay -Qqe` List explicitly installed packages

## Firefox for KDE Plasma
Chromium based browsers make use of kdialog for file dialogs. Firefox does not.
OpenSUSE created a patched firefox which integrates better into the KDE Plasma Desktop.
```
yay -S firefox-kde-opensuse-rpm
```

## If you want a graphical package manager
📦 I recommend only to use ```yay``` to update and install packages but (especially if you are a beginner) you may want a graphical package manager
- Simple GTK: ```yay -S gnome-packagekit```
- Simple Qt: ```yay -S apper```
- Complex GTK: ```yay -S pamac-aur```
- Complex Qt: ```yay -S octopi```

## If you use a GTK desktop and want Qt apps to use your GTK Theme
🧮 This may not look good with every GTK Theme
```
yay -S qt5-styleplugins
echo "export QT_QPA_PLATFORMTHEME=gtk2" >> ~/.profile
```

## If you want to read APFS Partitions
💽 If you have a Hackintosh installation you can use this to access your files from it
```
yay -S linux-apfs-dkms-git
```

## Graphics card configuration tool

### AMD
```
yay -S radeon-profile-git radeon-profile-daemon-git
systemctl enable --now radeon-profile-daemon
```
### NVIDIA
```
yay -S nvidia-settings
```

## Fonts

### General Fonts
🗛 Those are some essential font packages
```
yay -S adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans font-mathematica noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation ttf-linux-libertine
```

### Windows Fonts
🗛 If you want the Windows/Microsoft fonts (f.e. for Office Suites and required by certain games under Wine)
```
git clone https://aur.archlinux.org/ttf-ms-win10.git
cd ttf-ms-win10
```
READ PKGBUILD and copy all windows files into the directory and then run `makepkg -rsi`

### macOS Fonts
🗚 If you want the San Francisco Font by Apple
```
yay -S otf-san-francisco-pro otf-san-francisco-mono
```

## Nano syntax highlighting
📃 This package provides syntax highlighting enhancements to the nano text editor
```
yay -S nano-syntax-highlighting
```

## Auto clean package cache
🗑️ This will clear the package cache to only keep 1 version after every action

```
sudo mkdir /etc/pacman.d/hooks
sudo nano /etc/pacman.d/hooks/clean_package_cache.hook
```

```
[Trigger]
Operation = Upgrade
Operation = Install
Operation = Remove
Type = Package
Target = *
[Action]
Description = Cleaning pacman cache...
When = PostTransaction
Exec = /usr/bin/paccache -rk 2
```

## Theming

If you are using KDE Plasma, I do not recommend using the built-in installation methods, as in my experience they're very buggy.

### General
Icon Theme
```
yay -S la-capitaine-icon-theme
```
Cursor Theme
```
yay -S capitaine-cursors
```

### Plasma & Qt
Plasma, Kvantum, SDDM Style
```
yay -S kvantum-qt5 mcmojave-kde-theme-git
```
Color
```
yay -S materia-kde
```
Wallpaper
```
yay -S dynamic-wallpaper-mojave-kde-git dynamic-wallpaper-catalina-kde-git
```
Window Decoration
```
yay -S hello-kde-git
```
Effects
```
yay -S kwin-effects-appear1 kwin-effects-disappear1 kwin-effects-yet-another-magic-lamp kwin-scripts-forceblur
```
Latte Dock
```
yay -S latte-dock kwin-scripts-window-colors
```

### GTK & GNOME
GTK Theme
```
yay -S mojave-gtk-theme
```
Wallpaper
```
yay -S dynamic-wallpaper-mojave-gnome-timed-git dynamic-wallpaper-catalina-gnome-timed-git
```

# 12. Some fixes and tweaks

## Compatibility tweaks
🐛 This will fix some bugs and compatibility issues
```
sudo ln -sf /usr/lib/libncursesw.so.6 /usr/lib/libtinfo.so.5
yay -S libsndio-61-compat
```
### Spotify local files
```
yay -S ffmpeg-compat-57 ffmpeg
```

## Fix on shutdown "Failed to start user manager service for user 174" (sddm)
```
sudo chage --expiredate -1 sddm
```

## Force Color Emoji
```
yay -S ttf-joypixels
```
If the default font includes some emoji characters, they will be used over the characters provided by a dedicated emoji font, resulting in inconsistent display. Use the following config to enforce rendering emojis via JoyPixels. 
> ⚠️ Be aware that there is a bug when you do not have the [Windows Fonts](#windows-fonts) installed. See <https://bugs.archlinux.org/task/66080>

```
sudo nano /etc/fonts/conf.d/75-joypixels.conf
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

    <!--
    Treat this file as a reference and modify as necessary if you are not satisfied with the results.


    This config attempts to guarantee that colorful emojis from JoyPixels will be displayed,
    no matter how badly the apps and websites are written.

    It uses a few different tricks, some of which introduce conflicts with other fonts.
    -->


    <!--
    This adds a generic family 'emoji',
    aimed for apps that don't specify specific font family for rendering emojis.
    -->
    <match target="pattern">
        <test qual="any" name="family"><string>emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <!--
    This adds JoyPixels as a final fallback font for the default font families.
    In this case, JoyPixels will be selected if and only if no other font can provide a given symbol.

    Note that usually other fonts will have some glyphs available (e.g. Symbola or DejaVu fonts),
    causing some emojis to be rendered in black-and-white.
    -->
    <match target="pattern">
        <test name="family"><string>sans</string></test>
        <edit name="family" mode="append"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test name="family"><string>serif</string></test>
        <edit name="family" mode="append"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test name="family"><string>sans-serif</string></test>
        <edit name="family" mode="append"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test name="family"><string>monospace</string></test>
        <edit name="family" mode="append"><string>JoyPixels</string></edit>
    </match>

    <!--
    If other fonts contain emoji glyphs, they could interfere and make some emojis rendered in wrong font (often in black-and-white).
    For example, DejaVu Sans contains black-and-white emojis, which we can remove using the following trick:
    -->
    <match target="scan">
        <test name="family" compare="contains">
            <string>DejaVu</string>
        </test>
        <edit name="charset" mode="assign" binding="same">
            <minus>
                <name>charset</name>
                <charset>
                    <range>
                        <int>0x1f600</int>
                        <int>0x1f640</int>
                    </range>
                </charset>
            </minus>
        </edit>
    </match>

    <!--
    Recognize legacy ways of writing JoyPixels family name.
    -->
    <match target="pattern">
        <test qual="any" name="family"><string>EmojiOne</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Emoji One</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>EmojiOne Color</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>EmojiOne Mozilla</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <!--
    Use JoyPixels when other popular fonts are being specifically requested.

    It is quite common that websites would only request Apple and Google emoji fonts.
    These aliases will make JoyPixels be selected in such cases to provide good-looking emojis.

    This obviously conflicts with other emoji fonts if you have them installed.
    -->
    <match target="pattern">
        <test qual="any" name="family"><string>Apple Color Emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Segoe UI Emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Segoe UI Symbol</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Noto Color Emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>NotoColorEmoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Android Emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Noto Emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Twitter Color Emoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Twemoji</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Twemoji Mozilla</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>TwemojiMozilla</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>EmojiTwo</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Emoji Two</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>EmojiSymbols</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>

    <match target="pattern">
        <test qual="any" name="family"><string>Symbola</string></test>
        <edit name="family" mode="assign" binding="same"><string>JoyPixels</string></edit>
    </match>
</fontconfig>
```

## Desktop icons for nemo
```
gsettings set org.nemo.desktop show-desktop-icons true
```

## Backup / Restore

## System

I recommend Timeshift to backup your system. Install it with
```
yay -S timeshift cronie
systemctl enable --now cronie
```
For more information please refer to <https://github.com/teejee2008/timeshift>

## Packages / Services List

See <https://wiki.archlinux.org/index.php/Pacman/Tips_and_tricks#List_of_installed_packages>

### Backup
```
yay -Qqe > pkglist.txt
systemctl list-unit-files --state=enabled > enabled-services.txt
```
### Restore
```
yay -S --needed - < pkglist.txt
# Re-enable services with systemctl enable
```
