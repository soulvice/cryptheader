## collection of installation scripts

#### encrypt2
Enables the use for a detached header when using dm-crypt.

Used similar to 'cryptdevice=' for you boot flags, "cryptheader=\<device>:\<device-format>:\<file-location-on-device>".
For example (storing the key and header on a seperate device. ie: usb-thumbdrive):

"cryptdevice=/dev/sda1:cryptdevice cryptkey=/dev/sdb1:ext4:/crypt.key cryptheader=/dev/sdb1:ext4:/crypt.header root=/dev/mapper/cryptdevice-system ro rootfstype=btrfs rootflags=subvol=root"


**Note:** It's a good idea when using this to keep it named 'encrypt2', just incase mkinitcpio\dm-crypt receives an update it doesn't break your detached header loading. 
