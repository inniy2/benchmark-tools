## Benchmark tools  
- - - -  
# DD
- [dd](https://www.thomas-krenn.com/en/wiki/Linux_I/O_Performance_Tests_using_dd)  

- Usage  
```bash
dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=1G count=1 oflag=direct

dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=2G count=1 oflag=direct

dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=2G count=2 oflag=direct

dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=2G count=2 oflag=direct iflag=fullblock

dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=1G count=10 oflag=direct iflag=fullblock

dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=1G count=50 oflag=direct iflag=fullblock

dd if=/dev/zero of=/MYSQL/tmp/testfile  bs=1G count=100 oflag=direct iflag=fullblock

dd if=/dev/zero of=/tmp/testfile  bs=1G count=100 oflag=direct iflag=fullblock

dd if=/dev/zero of=/tmp/testfile  bs=1G count=100 oflag=dsync iflag=fullblock
```

# FIO  
- [fio](https://www.binarylane.com.au/support/solutions/articles/1000055889-how-to-benchmark-disk-i-o)  

- Installation  
```bash
cd /tmp

yum install -y make gcc libaio-devel wget

wget https://github.com/Crowd9/Benchmark/raw/master/fio-2.0.9.tar.gz ; 

tar xf fio-2.0.9.tar.gz

cd fio-2.0.9

make
```

- Usage  

- Random read/write performance  
```bash
fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randrw --rwmixread=75
```

- Random read performance  
```bash
fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randread
```

- Random write performance  
```bash
fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=test --filename=test --bs=4k --iodepth=64 --size=4G --readwrite=randwrite
```

# IOPING  

- Installation  
```bash
cd /tmp

wget http://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/i/ioping-1.1-1.el7.x86_64.rpm

rpm -ivh ioping-1.1-1.el7.x86_64.rpm

```

- Usage
```bash
ioping -c 10 .
```




