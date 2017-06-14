## multicrypt

**VERY MUCH A WIP**

Allows for multiple luks encrypted devices to be decrypted by a single "passport" file.
Passport file contains configurations for the luks crypt devies, such as: the device, their file type\format, their name,
root device, boot flags, boot filesytem type\format. 

Values are **export**ed for boot flags: root, rootfstype, rootflags

### Hook
  multicrypt_hook: **remove _hook** and place file in /usr/lib/initramfs/hooks/

### Install
  multicrypt_install: **remove _install** and place file in /usr/lib/initramfs/install

### mkinitcpio.conf
  HOOKS="...lvm2 multicrypt filesystems..."

### boot file options
  #### refind.conf
    options "passportdevice=<device>:<fstype>:<file> ro"


