# ZFS (Zettabyte File System)

## 介紹

### vdev

### zpool


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


## 參考資料

* [arch linux - zfs](https://wiki.archlinux.org/index.php/ZFS)
* [freebsd - zfs](https://www.freebsd.org/doc/zh_TW/books/handbook/zfs.html#zfs-differences)
