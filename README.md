# ubuntu_Kernel_rollback

******Revert to Old Kernel | Change Default Boot Kernel | Boot With Old (Previous) Linux Kernel*******

<p>-------------------------------------------------------------<br>
Step 1: Get currently installed kernel menu entries from GRUB configuration file.
<P>$ sudo cat /boot/grub/grub.cfg | grep -iE "menuentry 'Ubuntu, with Linux" | awk '{print i++ " : "$1, $2, $3, $4, $5, $6, $7}'
(or)</P><P><br>
$ sudo grub-mkconfig | grep -iE "menuentry 'Ubuntu, with Linux" | awk '{print i++ " : "$1, $2, $3, $4, $5, $6, $7}'</p>
</P>

<p>-------------------------------------------------------------<br>
Step 2: Modify the GRUB_DEFAULT=0 value as per your need.<br>
$ grep GRUB_DEFAULT /etc/default/grub<br>
$ sudo sed -i -e 's/GRUB_DEFAULT=0/GRUB_DEFAULT="1>2"/g' /etc/default/grub<br>
$ sudo grep GRUB_DEFAULT /etc/default/grub
</p
<p>-------------------------------------------------------------<br>
Step 3: Regenerate GRUB config file with modified settings.<br>
$ sudo update-grub<br>
</p>
<p>------------------------------------------------------------<br>
Step 4: Reboot the ubuntu and validate booted kernel.<br>
$ sudo systemctl reboot<br>
$ uname -srn<br>
</p>
<p>-------------------------------------------------------------<br>
important kernel related configuration files<br>
$ ls -l /boot/vmlinuz-*<br>
$ ls -l /boot/initrd.img-*<br>
$ dpkg --list | grep linux-image<br>
$ cat /etc/default/grub<br>
$ cat /boot/grub/grub.cfg<br>

-------------------------------------------------------------<br>
</p>
