### For proxmox - resize lvm disk
first increase vm disk from  GUI console.

### Console vm (ubuntu vm)
1. check disk size and number of partition
```shell
sudo fdisk -l
```
2. Extend physical drive partition
```shell
sudo growpart /dev/sda 3
```
3. Check phisical drive size
```shell
sudo pvdisplay
```
4. Resize LVM disk
```shell
sudo pvresize /dev/sda3
```
5. Check physical drive if has changed
```shell
sudo pvdisplay
```
6. Check Logical  volume size and name
```shell
sudo lvdisplay
```
7. Resize LV
```shell
sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
```
8. Check Logical  volume if has changed
```shell
sudo lvdisplay
```
9. Resize Filesystem
```shell
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv
```
10. Check Filesystem if has changed
```shell
sudo df -h
```
