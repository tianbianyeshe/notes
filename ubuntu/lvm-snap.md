# 利用lvm2对系统和文件快照
```bash
#查看
lvs
# 创建
lvcreate -s -n snap_name -L 20G /dev/ubuntu-vg/root
# 恢复
lvconvert --merge /dev/ubuntu-vg/snap_name
  #or
  lvconvert --merge /dev/mapper/ubuntu--vg-snap
rboot
# 取消快照
lvremove /dev/ubuntu-vg/snap_name
```
```bash
#各类查看
df -h
df -Th
```
