# Centos7Baseurlissue_solved
cd /etc/
cd yum.repos.d
ls
rm *
and answer to delete all by entering y
vi  CentOS-Base.repo
COPY the bellow code to input this code on the vi editor
and save the file 

````[base]
    name=CentOS-$releasever - Base
    baseurl=https://vault.centos.org/7.9.2009/os/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
    enabled=1

    [updates]
    name=CentOS-$releasever - Updates
    baseurl=https://vault.centos.org/7.9.2009/updates/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
    enabled=1

    [extras]
    name=CentOS-$releasever - Extras
    baseurl=https://vault.centos.org/7.9.2009/extras/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
    enabled=1

    [centosplus]
    name=CentOS-$releasever - Plus
    baseurl=https://vault.centos.org/7.9.2009/centosplus/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
    enabled=0
````
run yum update command and enter the direction as request
yum install wget
