## collection of installation scripts

#### encrypt2
Enables the use for a detached header when using dm-crypt.

Used similar to 'cryptdevice=' for you boot flags, "cryptheader=\<device>:\<device-format>:\<file-location-on-device>".
For example (storing the key and header on a seperate device. ie: usb-thumbdrive):

"cryptdevice=/dev/sda1:cryptdevice cryptkey=/dev/sdb1:ext4:/crypt.key cryptheader=/dev/sdb1:ext4:/crypt.header root=/dev/mapper/cryptdevice-system ro rootfstype=btrfs rootflags=subvol=root"


**Note:** It's a good idea when using this to keep it named 'encrypt2', just incase mkinitcpio\dm-crypt receives an update it doesn't break your detached header loading. 


**Steps**

1. cd /usr/lib/initramfs/install
2. git clone https://github.com/soulvice/cryptheader.git
3. cp /usr/lib/initramfs/hook/encrypt{,2}
4. nano /etc/mkinitcpio.conf
5. in 'BINARIES' add the format of your drive holding the key and cryptheader files. ie: ext4, fat, etc....
6. change your 'HOOKS' line to look like 'HOOKS=".....keyboard lvm2 encrypt2...."'
7. Ctl+O and Ctl+X then perform your 'mkinitcpio -p linux' call to rebuild your 'initramfs-*.img'


**Ideas**
- Have the header and the key file merge in to a single 'passport' file and encrypted with AES.
- Could use the computers mac address to salt the encrypted 'passport' file.....
