# PhotonOS 擴增磁區空間

## 偵測新硬碟空間
```
# echo 1 > /sys/class/block/sda/device/rescan
```
## 透過parted管理/dev/sda的磁區空間 
```
# parted /dev/sda
```
## 顯示目前磁區的使用
```
(parted)print
```
## 擴增目前的磁區空間 
```
(parted) resizepart 2 yes 100%
```
## 重新啟動
```
# reboot now
```
