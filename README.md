# CentOS 7 Yum BaseURL Error Fix (Vault Repo Solution)

## Problem
CentOS 7 has reached End of Life (EOL), and the standard Yum repository links (e.g., `mirror.centos.org`) no longer work. Running `yum update` or `yum install` may return:

```
Cannot find a valid baseurl for repo: base/7/x86_64
```

##  Solution

### Step 1: Navigate to the Yum repo directory

```bash
cd /etc/yum.repos.d
ls
rm *  # Press 'y' to confirm deletion of all files
```

### Step 2: Create a new repo file

```bash
vi CentOS-Base.repo
```

>  Sample Screenshots  
> ![Screenshot 1](https://github.com/user-attachments/assets/702ef1e1-0975-4e06-9439-1bc2ec35eba6)  
> ![Screenshot 2](https://github.com/user-attachments/assets/3dc99457-efc0-42f9-9f40-128b6f90cfaa)

### Step 3: Paste the following into the `vi` editor and save

```
[base]
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
```

### Step 4: Clean and update Yum

```bash
sudo yum clean all
sudo yum update
yum install wget
```

> Update Process Screenshot  
> ![Update Screenshot](https://github.com/user-attachments/assets/e78a1376-17a4-4f96-8c4c-ebcd2d234b66)
