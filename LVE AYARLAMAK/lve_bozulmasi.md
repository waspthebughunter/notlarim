```
[ 0.6792881 amd_gpio AMD 10030:00: Invalid config param 0014 Timed out for waiting the udeu queue being empty. Found volume group "pue" using metadata type lum2 Activation of logical volume pue/data is prohibited while logical volume pue/data_tmeta is active. Activation of logical volume pue/um-100-disk-0 is prohibited while logical volume pue/data_tmeta is active. Activation of logical volume pue/um-101-disk-0 is prohibited while logical volume pue/data_tmeta is active. Activation of logical volume pue/um-102-disk-0 is prohibited while logical volume pue/data_tmeta is active. Activation of logical volume pue/um-102-disk-1 is prohibited while logical volume pue/data_tmeta is active. 2 logical volume (s) in volume group "pve" now active


root@somewhere:~# lsblk
NAME               MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda                  8:0    0 465.8G  0 disk 
├─sda1               8:1    0  1007K  0 part 
├─sda2               8:2    0     1G  0 part /boot/efi
└─sda3               8:3    0 464.8G  0 part 
  ├─pve-swap       253:0    0     8G  0 lvm  [SWAP]
  ├─pve-root       253:1    0    96G  0 lvm  /
  ├─pve-data_tmeta 253:2    0   3.4G  0 lvm  
  └─pve-data_tdata 253:3    0   1.2T  0 lvm  
sdb                  8:16   0 931.5G  0 disk 
└─sdb1               8:17   0 931.5G  0 part 
  └─pve-data_tdata 253:3    0   1.2T  0 lvm
  

root@somewhere:~# lvchange -an pve/data_tmeta
root@somewhere:~# lvchange -an pve/data_tdata
root@somewhere:~# vgchange -ay



  7 logical volume(s) in volume group "pve" now active
root@somewhere:~#

```
