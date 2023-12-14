# ubuntu_Kernel_rollback

******Revert to Old Kernel | Change Default Boot Kernel | Boot With Old (Previous) Linux Kernel*******

-------------------------------------------------------------
Step 1: Get currently installed kernel menu entries from GRUB configuration file.
$ sudo cat /boot/grub/grub.cfg | grep -iE "menuentry 'Ubuntu, with Linux" | awk '{print i++ " : "$1, $2, $3, $4, $5, $6, $7}'
(or)
$ sudo grub-mkconfig | grep -iE "menuentry 'Ubuntu, with Linux" | awk '{print i++ " : "$1, $2, $3, $4, $5, $6, $7}'

-------------------------------------------------------------
Step 2: Modify the GRUB_DEFAULT=0 value as per your need.
$ grep GRUB_DEFAULT /etc/default/grub
$ sudo sed -i -e 's/GRUB_DEFAULT=0/GRUB_DEFAULT="1>2"/g' /etc/default/grub
$ sudo grep GRUB_DEFAULT /etc/default/grub

-------------------------------------------------------------
Step 3: Regenerate GRUB config file with modified settings.
$ sudo update-grub

-------------------------------------------------------------
Step 4: Reboot the ubuntu and validate booted kernel.
$ sudo systemctl reboot
$ uname -srn

-------------------------------------------------------------
important kernel related configuration files
$ ls -l /boot/vmlinuz-*
$ ls -l /boot/initrd.img-*
$ dpkg --list | grep linux-image
$ cat /etc/default/grub
$ cat /boot/grub/grub.cfg

-------------------------------------------------------------
