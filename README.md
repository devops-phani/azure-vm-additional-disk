# azure-vm-additional-disk

Ref
- https://learn.microsoft.com/en-us/azure/virtual-machines/linux/attach-disk-portal

```
lsblk 

parted /dev/sda --script mklabel gpt mkpart xfspart xfs 0% 100%
mkfs.xfs /dev/sda1
partprobe /dev/sda1

mkdir -p /var/lib/rancher/k3s/storage

mount /dev/sda1 /var/lib/rancher/k3s/storage

blkid

sudo nano /etc/fstab

UUID=b53aaf34-9302-4d05-b31a-b60c300239d2   /var/lib/rancher/k3s/storage   xfs   defaults,nofail   1   2

lsblk -o NAME,HCTL,SIZE,MOUNTPOINT | grep -i "sd"
```
