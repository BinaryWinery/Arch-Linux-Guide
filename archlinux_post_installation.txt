1. IN CHROOT
------------

configure localization :
>> locale-gen
>> echo "LANG=en_US.UTF-8" > /etc/locale.conf

Set hostname:
>> echo "yourhostname" > /etc/hostname

configure network :
>> pacman -S networkmanager
>> systemctl enable NetworkManager

install and enable sudo :
>> pacman -S sudo

install a bootloader :
::>> pacman -S grub
::>> grub-install --target=i386-pc /dev/sda  # Replace /dev/sda with your actual disk
::>> grub-mkconfig -o /boot/grub/grub.cfg

exit (out of chroot) :
>> exit

unmount filesystem : 
>> umount -R /mnt

now reboot system : 
>> reboot


2 . STUCK IN (pacman -Syu) : (mirror problem)
----------------------------------------------
change mirror : 

backup : 
>> sudo cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.backup

install reflector (for automatically sort the mirrors based on speed and reliability): 
>> sudo pacman -S reflector

set the mirror :
>> sudo reflector --latest 10 --sort rate --save /etc/pacman.d/mirrorlist





3 . FIX VMWARE NO FULL SCREEN
------------------------------

install open-vm-tools :
>> sudo pacman -S open-vm-tools

enable : 
>> sudo systemctl enable --now vmtoolsd

reboot : 
>> sudo reboot


4 . INSTALL YAY
----------------
update :
>> sudo pacman -Syu

install base-devel :
>> sudo pacman -S --needed base-devel git

clone yay git repo :
>> git clone https://aur.archlinux.org/yay.git

goto yay directory :
>> cd yay

install yay :
>> makepkg -si
