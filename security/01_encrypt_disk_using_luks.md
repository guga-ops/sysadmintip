# Tutorial Encrypt Disk with Luks

Tutorial to format disk using LUKS in Centos 7

## Getting Started


### Prerequisites

We need to install the cryptsetup-luks package

```bash
  yum install cryptsetup-luks
```

### Step 1 Listing Partitions
First we need listing the partitions:
```bash
  fdisk -l
```
### Step 2 Encrypt Partition Selected

```bash
  cryptsetup -y -v luksFormat /dev/sdc
```
### Step 3 Open the partition using Password Configured

```bash
  cryptsetup luksOpen /dev/sdc bigdata01
  Enter passphrase for /dev/sdc:
```

### Step 4 Listing the 
```bash
  ls -l /dev/mapper/bigdata01
  cryptsetup -v status backup2
```

### Step 5 
```bash
cryptsetup luksDump /dev/xvdc
```

### Step 6 Format Partition
```bash
  dd if=/dev/zero of=/dev/mapper/bigdata01
  pv -tpreb /dev/zero | dd of=/dev/mapper/bigdata01 bs=128M
  mkfs.ext4 /dev/mapper/bigdata01
  mkdir /backup2
  mount /dev/mapper/backup2 /backup2
  df -H
  cd /backup2
  ls -l
```

End with an example of getting some data out of the system or using it for a little demo

# Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Guga** - *SysAdminTip* - [SysAdminTipRepo](https://github.com/guga-ops/sysadmintip.git)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

