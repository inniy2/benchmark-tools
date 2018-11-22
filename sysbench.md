## SYSBENCH  
- - - -  
- [sysbench 1.0.15](https://github.com/akopytov/sysbench)  

- Installation: curl  
```bash
root> curl -s https://packagecloud.io/install/repositories/akopytov/sysbench/script.rpm.sh | sudo bash
root> sudo yum -y install sysbench
```

- Installation: cat
```bash
cat << EOF | tee /etc/yum.repos.d/akopytov_sysbench.repo
[akopytov_sysbench]
name=akopytov_sysbench
baseurl=https://packagecloud.io/akopytov/sysbench/el/7/\$basearch
repo_gpgcheck=1
gpgcheck=0
enabled=1
gpgkey=https://packagecloud.io/akopytov/sysbench/gpgkey
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt
metadata_expire=300

[akopytov_sysbench-source]
name=akopytov_sysbench-source
baseurl=https://packagecloud.io/akopytov/sysbench/el/7/SRPMS
repo_gpgcheck=1
gpgcheck=0
enabled=1
gpgkey=https://packagecloud.io/akopytov/sysbench/gpgkey
sslverify=1
sslcacert=/etc/pki/tls/certs/ca-bundle.crt
metadata_expire=300
EOF

sudo yum -y install sysbench
```



