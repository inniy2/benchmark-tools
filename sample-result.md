## Sample result  
- - - - 
# DD  
```bash
dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=1G count=50 oflag=direct iflag=fullblock
```
```
50+0 records in
50+0 records out
53687091200 bytes (54 GB) copied, 124.101 s, 433 MB/s
```

# FIO  
```bash
fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test--filename=test --bs=4k --iodepth=64 --size=40G --readwrite=randrw --rwmixread=75
```
```
test: (g=0): rw=randrw, bs=4K-4K/4K-4K, ioengine=libaio, iodepth=64
fio-2.0.9
Starting 1 process
test: Laying out IO file(s) (1 file(s) / 40960MB)
Jobs: 1 (f=1): [m] [100.0% done] [206.4M/69840K /s] [52.9K/17.5K iops] [eta 00m:00s]
test: (groupid=0, jobs=1): err= 0: pid=9962: Thu Nov 22 14:17:23 2018
  read : io=30717MB, bw=207776KB/s, iops=51944 , runt=151383msec
  write: io=10243MB, bw=69289KB/s, iops=17322 , runt=151383msec
  cpu          : usr=14.26%, sys=28.45%, ctx=9244919, majf=0, minf=6
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued    : total=r=7863455/w=2622305/d=0, short=r=0/w=0/d=0

Run status group 0 (all jobs):
   READ: io=30717MB, aggrb=207776KB/s, minb=207776KB/s, maxb=207776KB/s, mint=151383msec, maxt=151383msec
  WRITE: io=10243MB, aggrb=69289KB/s, minb=69289KB/s, maxb=69289KB/s, mint=151383msec, maxt=151383msec

Disk stats (read/write):
  sda: ios=7853261/2619603, merge=2450/671, ticks=7704222/1893038, in_queue=9622989, util=100.00%
```

# IOPING  
```bash
ioping -c 50 .
```
```
4 KiB <<< . (ext4 /dev/sda1): request=4 time=353.6 us
4 KiB <<< . (ext4 /dev/sda1): request=5 time=339.2 us
4 KiB <<< . (ext4 /dev/sda1): request=6 time=363.8 us
4 KiB <<< . (ext4 /dev/sda1): request=7 time=369.5 us (slow)
4 KiB <<< . (ext4 /dev/sda1): request=8 time=269.6 us
4 KiB <<< . (ext4 /dev/sda1): request=9 time=320.2 us
4 KiB <<< . (ext4 /dev/sda1): request=10 time=387.5 us (slow)
4 KiB <<< . (ext4 /dev/sda1): request=11 time=291.7 us
4 KiB <<< . (ext4 /dev/sda1): request=12 time=385.7 us (slow)
4 KiB <<< . (ext4 /dev/sda1): request=13 time=311.6 us
4 KiB <<< . (ext4 /dev/sda1): request=14 time=3.47 ms (slow)
4 KiB <<< . (ext4 /dev/sda1): request=15 time=289.5 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=16 time=387.2 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=17 time=315.5 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=18 time=384.5 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=19 time=314.6 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=20 time=351.0 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=21 time=224.9 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=22 time=325.4 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=23 time=314.6 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=24 time=361.7 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=25 time=312.8 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=26 time=383.1 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=27 time=313.4 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=28 time=340.3 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=29 time=223.5 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=30 time=184.8 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=31 time=297.2 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=32 time=275.2 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=33 time=277.8 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=34 time=290.1 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=35 time=298.7 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=36 time=342.6 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=37 time=340.1 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=38 time=342.0 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=39 time=365.0 us
4 KiB <<< . (ext4 /dev/sda1): request=40 time=382.8 us
4 KiB <<< . (ext4 /dev/sda1): request=41 time=366.1 us
4 KiB <<< . (ext4 /dev/sda1): request=42 time=363.8 us
4 KiB <<< . (ext4 /dev/sda1): request=43 time=366.0 us
4 KiB <<< . (ext4 /dev/sda1): request=44 time=328.2 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=45 time=346.7 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=46 time=360.4 us
4 KiB <<< . (ext4 /dev/sda1): request=47 time=366.8 us
4 KiB <<< . (ext4 /dev/sda1): request=48 time=364.1 us
4 KiB <<< . (ext4 /dev/sda1): request=49 time=260.3 us (fast)
4 KiB <<< . (ext4 /dev/sda1): request=50 time=238.5 us (fast)

--- . (ext4 /dev/sda1) ioping statistics ---
49 requests completed in 19.1 ms, 196 KiB read, 2.57 k iops, 10.0 MiB/s
generated 50 requests in 49.0 s, 200 KiB, 1 iops, 4.08 KiB/s
min/avg/max/mdev = 184.8 us / 389.6 us / 3.47 ms / 446.9 us
```
