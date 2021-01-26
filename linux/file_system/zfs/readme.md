# ZFS (Zettabyte File System)

## 介紹

### vdev (virtual device)

是用來組合成pool的最基本單位
以下是vdev的類型
* block device (i.g. /dev/sda, /dev/sda1)
* file (i.g. /tmp/file1)
* mirror
* raidz, raidz2, raidz3
* log
* cache
* spare

![zfs-vdev](https://github.com/chenghung/wiki/blob/master/linux/file_system/zfs/zfs-vdev-3.png)

### zpool

zpool是由至少一個vdev所組成

![zfs-zpool](https://github.com/chenghung/wiki/blob/master/linux/file_system/zfs/zfs-pool-vdev-disk.png)

## 安裝

arch linux
```
$ yay -S linux510-zfs
$ zfs --version
zfs-kmod-2.0.1-1
```

## 問題排除

### 開機後沒有自動import/mount zfs

發現重新開機後,沒有自動mount zfs, 必須要手動執行import

先把建好的pool設定寫入到設定檔
```
$ zpool set cachefile=/etc/zfs/zpool.cache my-test-pool
```

啟動自動import所需要的service
```
$ systemctl enable zfs-import-cache
$ systemctl enable zfs-import.target

```

啟動自動mount所需要的service
```
$ systemctl enable zfs-mount
$ systemctl enable zfs.target
```

重新開機即可
```
$ sudo reboot
```

### 加了新的vdev到pool後, zfs檔案系統的available size沒有增加


預設zfs並沒有打開autoexpand
所以加了一個新的vdev進到pool, 並不會自動調整available size
```
$ sudo zpool get autoexpand test5
NAME   PROPERTY    VALUE   SOURCE
test5  autoexpand  off      local
```

可以透過下列指令打開autoexpand
```
$ sudo zpool set autoexpand=on test5
```


### 無法從pool移除vdev

```
$sudo zpool remove test5 /file3
cannot remove /file3: out of space
```

有兩個可能的原因
* 現在存放的資料超過移除後的總容量上限
* vdev的size太小, 建議至少使用1G以上


## 參考資料

* [arch linux - zfs](https://wiki.archlinux.org/index.php/ZFS)
* [freebsd - zfs](https://www.freebsd.org/doc/zh_TW/books/handbook/zfs.html#zfs-differences)
* [zfs - 101 (這篇介紹很詳細, 推薦)](https://arstechnica.com/information-technology/2020/05/zfs-101-understanding-zfs-storage-and-performance/)
* [migrate data to zfs mirror](https://jrs-s.net/2020/03/10/rebalancing-data-on-zfs-mirrors/)
